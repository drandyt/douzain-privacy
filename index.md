# Douzain — Privacy Policy

**Last updated:** 26 July 2026

Douzain ("the game", "we", "us") is a tactical augmented-reality strategy game published by
**Studio Douzain**, contactable at **studio.douzain@gmail.com**. This
policy describes what the app actually does with data, based on a line-by-line audit of the
shipping code — not a generic template.

---

## Summary

- **No account is required to play.** There is no sign-up, no login, no password.
  - **We do not show ads and do not use any advertising or analytics SDK.** The only
  third-party network dependency in the app is Sentry (crash reporting — see §4).
  - **We never sell data to anyone**, and there are no in-app purchases or real-money
  transactions of any kind in this app.
- **The camera** is used live, on-device, to render the augmented-reality view. No camera
  frame is ever saved to a file, encoded to an image, or sent anywhere.
  - **Location** is read once per AR session, coarsely, to bias *which creature species*
  appears near you. It is used entirely on your device and — as of this audit — never
  leaves it. See §2 for the full detail and the one caveat we flag.
- **If you opt in** (off by default), we collect anonymous play-session and progress data
  to improve the game. You can withdraw at any time in About; withdrawal stops collection
  immediately. See §5.
- **If you play online multiplayer**, your device sends match moves, and the player name
  you choose to type, to our relay server so your opponent's device can follow the match.
  See §6 — this section flags a real finding: the display name you type is **not**
  anonymised, so please don't type your real name if you'd rather not share it.
- **Creature captures are registered to a permanent server-side ledger** ("The Great
  Ledger") that gives each captured coin a unique serial number. This is new (landed
  2026-07-18) and is **not currently deletable on request** — see §7, flagged for owner
  attention.
- **Crash reports** go to Sentry, a third-party error-monitoring service, with personal-data
  collection explicitly disabled in our configuration. See §4.

---

## 1. Camera

Douzain uses your device's camera to show creatures overlaid on the real world in
augmented-reality (AR) mode. The feed is decoded by the browser/WebView engine and drawn
straight to the screen (`getUserMedia`). **No camera image is ever captured, saved, recorded
or uploaded anywhere.**

AR mode does let you take an in-game **snapshot**, which is saved on your device only (never
uploaded). A snapshot can never contain camera imagery: it is available only when the AR
slider is fully into the virtual "serein" view, and the code that builds the picture has no
access to the camera at all, so a real-world photo cannot be produced even by mistake. A
snapshot is held in memory and discarded unless you explicitly choose to save it.

You can decline the camera permission; AR mode will be unavailable, but story mode, the
hex-board battle game, the collection screen, and multiplayer all work without it.

## 2. Location

**Permission requested:** coarse location only (`ACCESS_COARSE_LOCATION`). Douzain does
**not** request fine/precise location.

**What it's used for:** once you open the AR lens, the app makes a single, non-blocking,
best-effort request for your approximate coordinates
(`enableHighAccuracy:false`, so it can only ever return a coarse fix).
That coordinate is run through a small **offline** lookup table (bounding boxes for named
regions + a latitude-based climate band — no network call, no third-party geocoding
service) that turns it into coarse tags like `"scandinavia"` or `"desert"`.
Those tags are used **only** to nudge which creature species is more likely to appear
near you (e.g. a colder region favours different creatures than a desert one). They do
**not** affect which terrain/scenery renders — that is driven by your capture count, not
location.

**Does location ever leave the device?** As of this audit: **no.**
- The coordinate and the derived tags are held in an in-memory module cache
  (`js/ar/lens/gps.js`), never written to `localStorage`, and never appear in any
  telemetry event: `recordEvent()` defensively strips any key that looks like a location
  field (`lat`, `lng`, `lon`, `coords`, `geo`, etc.) before anything is queued, and the one
  AR event that fires on a real capture (`'capture'`) carries only species/isNew/
  collection-count/source fields.
  - We searched the multiplayer relay client code for any coordinate field and found none —
  match data is moves/board state only (§6).
- The new creature-registration system ("Great Ledger," §7) has a hook that *could* attach
  a region tag to a registration in a future build (`setMintContextProvider` in
  `js/data/collection.js:206-227`), but as shipped **that hook is never called anywhere in
  the game** — we grepped the whole codebase for its one call site and found only the
  function definition. So today a coin registration carries no location signal at all.
  ⚠ **Flagging this as the one item to re-check before every future release**: if a later
  change wires that hook up, region-level tags (not raw coordinates) would start reaching
  our server, and this policy would need an update first.

You can decline the location permission; AR mode still works, it simply has no geographic
bias on species selection.

## 3. Online multiplayer relay

If you start or join an online match (live or "postal"/play-by-mail), your device
exchanges data with our relay server, a Cloudflare Worker we operate
(`tools/pvp-relay/cloudflare/src/worker.js`). This is covered in detail in §6.

## 4. Crash and diagnostic data (Sentry)

To find and fix crashes, Douzain uses **Sentry** (sentry.io), a third-party error-reporting
service, if the release build is configured with a Sentry key. Our initialisation
explicitly disables personal-data collection (`sendDefaultPii: false`) and does not enable
session replay or performance tracing.
A crash report can include: the error message and stack trace, the app release identifier,
and whatever device/OS metadata Sentry's SDK attaches by default (e.g. device model, OS
version, locale) under its standard (non-PII) error-reporting integrations.

⚠ **UNVERIFIED / caveat:** Sentry's browser SDK ships default "breadcrumb" integrations
(console messages, navigation, network request URLs) that we did not find explicitly
disabled in `js/sentry-init.js`. We searched the AR/location code for any `console.log`
that prints raw coordinates and found none — only distances in metres, ages, and error
messages — so we have no evidence breadcrumbs could leak a coordinate. But we did not
exhaustively audit every `console.*` call in the codebase, so this is a caveat, not a
guarantee.

Crash reporting **is active in the released build**: the build machine's `secrets.js`
carries a live Sentry key (independently re-verified 2026-07-26 by inspecting the actual
file on the release build machine, not inferred from documentation).

## 5. Optional anonymous gameplay analytics (opt-in, off by default)

The **first time you launch the app**, you are asked: *"May we collect anonymous gameplay
data to make Douzain better?"* — with an explicit **Allow** / **No thanks** choice. Nothing
is collected before you answer, and choosing "No thanks" collects nothing at all.

You can change this decision at any time from the **About** screen; the current state is
shown as "SHARING: ON/OFF."

**If you opt in**, we collect:
- **Session activity**: app open/close, session length.
- **Match results and progress**: e.g. a creature capture (species + whether it was your
  first + your collection size), a multiplayer match starting.
- **A compact save-data version snapshot** — a short technical string recording which
  local save formats are present and their version numbers, used to detect data-migration
  problems, not to read your actual save contents.
  - **A random per-install identifier** — not your name, account, or any hardware ID. It is
  a UUID generated on first launch and stored via the Capacitor Preferences API (survives
  a WebView cache clear, but is reset if you uninstall and reinstall the app).
  
**We defensively never collect raw location.** Any payload key shaped like a GPS field is
stripped before it's even queued locally, regardless of source.

**Where it goes:** if collected, batched events are sent over HTTPS to a Cloudflare Worker
we operate, which writes them as line-delimited JSON files into a private Cloudflare R2
storage bucket. The worker exposes **only** a write endpoint — there is no read, list, or
delete endpoint reachable from the app or the internet at large.

**Retention:** collected analytics data has no automatic expiry — we retain it until we
manually delete it. (Stated plainly rather than promising a retention window we have not
implemented.)

**Withdrawal:** turning collection off immediately stops future collection and **wipes any
event queued on your device that had not yet been sent**.
⚠ It does **not** retroactively delete batches that were already transmitted before you
withdrew — there is no mechanism in this codebase to identify and erase a specific
installation's already-sent, anonymous data, since the whole point of the identifier is
that we don't tie it to you. If you want a specific past submission removed, contact
**studio.douzain@gmail.com** and we will do our best on a manual basis.

A remote kill switch exists: if we ever need to shut this off server-side, the app is
told to stop permanently and wipe its local queue.

## 6. Online multiplayer — what actually transits the relay

Our multiplayer relay is a Cloudflare Worker with Durable Objects
(`tools/pvp-relay/cloudflare/src/worker.js`). It has no user accounts and no login.

When you create or join an online match, the following data is sent to the relay and held
for the lifetime of that match:
- A random per-install player ID (the same kind of anonymous identifier as §5, generated
  and stored locally — a different value from the telemetry ID, not linked to it).
  - **The display name you have chosen** (default "Player," editable, up to 32 characters).
  This is sent to the relay and shown to your opponent's device.
    ⚠ **This is a genuine finding worth your attention:** unlike everything else in this
  policy, the display name is free text you type. If you type your real name, that real
  name is transmitted to your opponent and stored (for the match's lifetime) on our
  server. **We recommend not using your real name as your display name if you'd rather it
  stay private.**
- Your in-game moves, army setup, and match/clock state — no other free-text field exists
  in the match protocol besides the display name above.
- An invite code (random letters) that acts as the match's address — not personally
  identifying.

**Retention:** a live match is deleted from the server after 2 hours of inactivity; a
postal (play-by-mail) match is kept for up to 30 days of inactivity; a match you close is
deleted about 60 seconds after closing.
A separate small database table tracks "whose turn is it" per match so the app can show
you a "your move" list; these turn-tracking rows (which contain only the anonymous player
ID and match code, no personal data) may be retained after the match itself expires.

## 7. Creature capture registry ("The Great Ledger") — new, landed 2026-07-18

When you capture a creature (in AR or in story mode), the app now registers that capture
with a server-side ledger so every captured creature gets a permanent, unique serial
number and edition stamp — similar in spirit to a coin mint's serial registry.

**What's sent:** the coin's ID, the species, the capture timestamp, and a "provenance"
object containing: the capture timestamp again, a model-version tag for that species, the
git build identifier of the app version you're running, and the same random per-install
player ID used for multiplayer (§6) — **not** your telemetry ID, and (per §2) currently
**no** location data.

**What the server stores, permanently:** the above, plus a server-assigned serial number,
a global sequence number, an "edition" label, and — if a signing key is configured — a
tamper-evident signature over the entry.

**This registry is permanent by design** — the same way a mint doesn't erase a coin's
serial number. Once a creature is captured, its registration (including your anonymous,
random player ID — never your name or contact details) is retained indefinitely on our
server, and there is no automatic way for a player to remove it from inside the app. If
this concerns you, contact **studio.douzain@gmail.com** and we will handle removal
requests manually on a best-effort basis.

## 8. Data we do not collect

We do not collect or process: your name (unless you choose to type it as your multiplayer
display name — see §6), email address, phone number, contacts, photo/media library,
financial or payment information, advertising identifiers, browsing history outside this
app, or any account credentials (there are no accounts to have credentials for).

## 9. Children

Douzain is intended for players aged 13 and up (matching the app's Google Play target
audience setting). We do not knowingly collect personal information from children under 13.

## 10. Permissions this app requests, and why

| Permission | Why | Leaves the device? |
|---|---|---|
| Internet | Crash reports (§4), optional telemetry (§5), multiplayer relay (§6), creature-capture registry (§7) | Only the data described in those sections |
| Camera | Live AR creature overlay (§1) | No |
| Coarse location | Biases which creature species appears in AR (§2) | No (see §2's one caveat) |
| Notifications | Local "your move" alerts for postal multiplayer matches (scheduled on your device, not pushed from a server) | No |
| Vibrate | Haptic feedback (button taps, alerts) | No |

## 11. Other third parties

The only third party this app sends any data to is **Sentry** (§4). The multiplayer relay
and telemetry endpoints (§5, §6, §7) are Cloudflare Workers **we operate ourselves** — data
sent there goes to our own infrastructure, not to an independent company, though it does
transit Cloudflare's network to reach it.

The app also uses Google Play's own **Asset Delivery** library to download a supplementary
content pack after install (a Google Play Store distribution feature, not an analytics or
advertising SDK — it has no code path that reads or sends gameplay/personal data).

We do not use any advertising network, analytics SDK (e.g. Firebase/Google Analytics), or
social-login SDK. This is based on the complete dependency list in `package.json` and
`android/app/build.gradle`, not a promise made without checking.

## 12. Changes to this policy

We may update this policy as the game changes. The "Last updated" date at the top will
change whenever we do, and material changes will be described here.

## 13. Contact

Questions about this policy or a data request: **studio.douzain@gmail.com**.

