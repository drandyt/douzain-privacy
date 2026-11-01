# Douzain — Privacy Policy

**Last updated:** 1 November 2026

Douzain ("the game", "we", "us") is a tactical creature game for Android and iPhone, made and published by
**Studio Douzain**. Studio Douzain is a single independent developer and is responsible for the
data described here. Contact: **studio.douzain@gmail.com**.

This policy describes what this version of the app actually does with data. It was written from
the app's code and from the settings of the server it talks to.

---

## Summary

- **No accounts.** There is no sign-up, no login, no password and no email address in the game.
  The game makes a random player ID on your phone.
- **Your player name is made by the game.** It is picked from a fixed list of names; you can ask
  for a different one until you lock one in. You cannot type your own name, so we never hold a
  name you typed.
- **No ads, no advertising or tracking SDKs, no social-login SDK, no in-app purchases.** We never
  sell data.
- **The camera** shows creatures through the Lens, live on your phone. No camera image is ever
  stored or sent.
- **Location** is read approximately, on your phone, to choose which creatures appear and to draw
  the sky in the Observatory. It never leaves your phone.
- **Online play** sends your player ID, player name, moves and game standing to our own server
  (Hetzner, Finland). Your player name and standing (rating, ladder points, crowns) are **shown
  publicly to other players** on the challenge board and the ranked ladder.
- **Every creature you capture is registered** on our server so it gets a serial number. Test
  builds use a test ledger that will be deleted before public launch (section 5).
- **Gameplay statistics and crash reports are optional.** Nothing is sent unless you tap Allow on
  the gameplay-data card, and you can change your mind at any time.
- **You can ask us to delete your data** by email; see section 10.

---

## 1. Camera

The Lens uses your phone's camera to show creatures beyond the veil. The camera feed is drawn
straight to the screen. **No camera image is ever saved, recorded or uploaded.**

You can take an in-game snapshot in the Lens. It is saved on your phone only, and it can only be
taken when the view is fully in Serein: it is built from the game's own 3D picture, never from
the camera, so it cannot contain a real-world photo.

You can refuse the camera permission. The Lens will not open, but story mode, battles, the
collection and online play all work without it.

## 2. Location

**Permission:** approximate location only. On Android the app asks for coarse location; on iPhone
it asks for location while using the app, with Precise Location off by default. It never reads
location in the background.

**When it is read:** when you open the Lens, and when you open the Observatory, the
app asks your phone once for an approximate position.

**What it is used for:** on your phone, the position is turned into broad tags (a region and a
climate band) with a lookup table built into the app; no map or geocoding service is called. The
tags make some creatures more or less likely to appear. The Observatory also uses the position to
work out the sky.

**Does it leave the phone?** No. The position is held in memory only, is never saved, is removed
from anything that could be sent (gameplay statistics strip any location field), and is not
included in creature registrations or online matches.

You can refuse the location permission. The Lens still works; creatures are then chosen without a
regional bias.

## 3. Your player ID and player name

- **Player ID.** On first launch the app makes a random ID on your phone. Settings → ACCOUNT shows
  a short form of it (it starts with `DZ-`). It is not linked to your phone's hardware, your
  Google account or anything else about you. It is used for online play, the ranked ladder and
  the creature registry.
- **Player name.** The game gives you a name from a fixed list of names. You can ask for a new
  one until you like it, then lock it in. Names are one word of up to eight letters. Because you
  cannot type a name, the game does not collect free text from you.

## 4. Online play

Each time the game opens, it asks our relay server whether any of your matches are waiting for
your move and fetches the ranked ladder; this sends your player ID (and the short handle made
from it), nothing else. If you start or join an online match, use the challenge board or play
ranked, your phone also sends the match data below. The relay server is a program we run on a server rented from **Hetzner Online GmbH in Helsinki,
Finland**. Cloudflare provides only our domain name (DNS) and holds no game data. All traffic is
encrypted (HTTPS).

**What is sent:** your player ID, your player name, your moves, army and match clock, and the
match's invite code (random letters). For ranked play, the app also sends a random key made on
your phone that signs your results, and your result, rating and ladder points. Online play has no
chat and no other free-text field.

**Who can see it:**
- Your opponent sees your player name and your moves.
- **Everyone** who opens the challenge board sees your posting: your player name, rating, ladder
  points and crowns.
- **Everyone** can see the ranked ladder: your player name (or a short handle made from your
  player ID), rating, points, wins and losses.

**How long it is kept:**
- A live match with no move for 10 minutes ends as abandoned; a play-by-mail match ends after 90
  days with no move. A finished or abandoned match is deleted 7 days after it ends.
- An invite nobody joins is deleted after about 2 hours (live) or about 3 days (play-by-mail).
- The list of your matches that are waiting for your move is deleted 60 days after it last
  changed.
- A challenge-board posting stays up until you withdraw it or it expires after 30 days; an
  expired posting is deleted a day later.
- Ranked results (wins, losses, rating, points) are kept so that everyone's ladder stays correct.
  They are kept until you ask us to delete your data; then we remove your name and player ID from
  them and move them to a new anonymous ladder entry (section 10).

**IP addresses:** the server uses your IP address to limit abuse (a cap on requests per minute).
Most of these limits live only in the server's memory. The limit on creature registrations is
written to the server's database for a few minutes, under your IP address alone, not linked to
your player ID; a backup taken in those minutes keeps it for that backup's life (section 10).

## 5. Creature registry ("the Great Ledger")

When you capture a creature, in the Lens or in story mode, the app registers it with our server so
that it gets a serial number. This happens whether or not you allow gameplay statistics, because
the serial number is part of the game.

**Test builds use a test ledger.** Serial numbers in test builds are not permanent: the whole test
ledger will be deleted before the game's public launch, and a new ledger starts then.

**What is sent:** the coin's ID, the species, the capture time, the app version, the creature's
model version and your player ID. No player name and no location.

**What is kept:** the above, plus the serial number, edition, a tamper-evident signature where
that is switched on, and the coin's history of owners by player ID. Registry entries can be read
by anyone who knows a coin's serial or a player ID. They are kept until the test ledger is
deleted. **If you ask us to delete your data sooner, we remove your player ID from every entry**:
the serial number, species and capture date remain, but no longer point to you.

## 6. Gameplay statistics (optional, off unless you allow it)

The first time you play, a card asks: *"May we collect gameplay data to make Douzain better?"*,
with **Allow gameplay data** and **No thanks**. Nothing is sent before you answer, and nothing is
sent if you choose No thanks. You can change your choice at any time in Settings → ABOUT.

**If you allow it, the app sends:**
- play sessions (app opened and closed, session length, the screen a session ended on);
- match results and progress (for example a capture, a story stage started or finished, an Arena
  match started or finished);
- in-game spending of the game's own currency (what you bought with it; there is no real money in
  the game);
- the app version and a short technical note of which save formats are on the phone;
- a random ID made on your phone for statistics only. It is a different value from your player
  ID and is not linked to it, to your name or to your location.

**Where it goes:** to our own server (the same Hetzner server, a separate database). Your IP
address is used only in memory, to limit abuse; it is not stored with the statistics.

**How long:** deleted automatically after **180 days**.

**Stopping and deleting:** turning sharing off in Settings → ABOUT stops it at once and deletes
anything not yet sent. **Delete my analytics data** (Settings → ABOUT) asks our server to erase
everything tied to your statistics ID; this can take a few days. Afterwards the server keeps only
that ID itself on a do-not-accept list, so late-arriving statistics are refused, until the 180-day
limit passes.

## 7. Crash reports (optional, same choice)

Crash reports start only if you tap **Allow gameplay data** on the card in section 6; if you
choose No thanks, no crash reports are sent. They go to **Sentry** (Functional Software, Inc.), a
crash-reporting service, and are stored in Sentry's **European Union** region for **30 days**.

While gameplay data is allowed, Sentry also receives a small "session" note each time the game
opens, so we can see what share of play sessions crash: the app version, phone model and whether
the session ended in a crash. It holds no player ID, name or location.

A crash report holds the error and where it happened in the code, the app version, the phone
model, operating-system version and language, and a short trail of recent app events. Sentry is set not to
store IP addresses, and before a report is sent the app removes player IDs, coin IDs and other
identifiers from its text. Crash reports never contain your player name or your location.

## 8. Notifications

If you allow notifications, the app may remind you, a few hours after you close the Lens, that a
creature you have not caught yet is nearby or that something new has appeared. These reminders
are scheduled on your phone; nothing is pushed from a server, and the reminder is not based on
your location. You can turn reminders off in Settings → NOTIFICATIONS or in your phone's settings.

## 9. Data on your phone, and phone backups

Your collection, progress, settings, player ID, player name and statistics ID are stored on your
phone. Uninstalling the app deletes them from the phone.

Android's own backup is turned on for this app. If backup is on in your phone's settings, Android
may copy the app's saved data (including your player ID, statistics ID and collection) to your
Google account's backup, under Google's terms. We cannot see or delete that copy; you can delete
it in your Google account's backup settings.

On iPhone, iCloud Backup and computer backups may include the app's saved data in the same way,
under Apple's terms. We cannot see or delete that copy; you can exclude the app in your iPhone's
iCloud settings.

## 10. How long we keep data, and how to have it deleted

**How to ask:** email **studio.douzain@gmail.com** from any address, with the subject **"Data
deletion request"**. Include your Player ID (Settings → ACCOUNT, starts with `DZ-`) if you have
it, your player name, and roughly when you last played. We reply to confirm and finish within
**30 days**. You do not need the game to ask. The full steps are also at
[relay.douzain.com/account/delete](https://relay.douzain.com/account/delete).

**What we delete:** your player name and player ID from our server, your online matches, your
list of matches waiting for a move, your challenge-board postings and everything else our server
holds under your player ID. Matches you were in are deleted whole, including your opponent's copy, even a match still in play.

**What we keep after a deletion:**
- Creature registry entries: the serial number, species and capture date, with your player ID
  removed (section 5).
- Ranked results: wins, losses and rating, with your name and player ID removed and moved to a
  new anonymous ladder entry, so your
  opponents' records stay correct.

**Retention at a glance:**

| Data | Kept for |
|---|---|
| Live match / play-by-mail match | until it ends (10 minutes / 90 days with no move), then 7 days |
| Unjoined invite | about 2 hours (live) / about 3 days (play-by-mail) |
| Matches-waiting-for-your-move list | 60 days after it last changed |
| Challenge-board posting | until withdrawn, at most 30 days, deleted a day after it expires |
| Ranked results | until you ask; then name and player ID removed |
| Creature registry entries | until the test ledger is deleted before public launch; on request your player ID is removed sooner |
| Gameplay statistics (if allowed) | 180 days, or sooner on Delete my analytics data |
| Crash reports (if allowed) | 30 days, at Sentry (EU region) |
| Server logs | 14 days |
| Server backups | nightly copies on the server for 14 days; an encrypted off-site copy (Hetzner, EU) deleted within six months; copies taken before server updates deleted after 90 days |

**Backups:** because of the backups above, data deleted from our server is gone from every copy
within six months.

**Server logs:** our server's logs can contain an IP address, a player ID or an invite code. They
are deleted automatically after 14 days.

**Your rights:** you can also ask us for a copy of your data or to correct it, at the same
address. If you are unhappy with how we handle your data, you can complain to the UK Information
Commissioner's Office (ico.org.uk) or your local data protection authority.

## 11. Other companies involved

- **Hetzner Online GmbH** (Germany; server in Finland) runs the server our relay and database are
  on, under a data processing agreement. Off-site backups are stored with Hetzner, encrypted.
- **Sentry / Functional Software, Inc.** receives crash reports if you allow them (section 7),
  under a data processing agreement; stored in the EU region.
- **Google** (Android) delivers the game's extra content through Play Asset Delivery when you
  install it, and runs Android's backup (section 9). Google does this under its own terms.
- **Apple** (iPhone) distributes the app through the App Store and TestFlight and runs iCloud
  Backup (section 9), under Apple's terms. We do not use Game Center sign-in in this version.
- **Cloudflare** provides our domain name service (DNS) only; game data does not pass through or
  stay with Cloudflare.

The app contains **no advertising SDK, no analytics SDK (such as Firebase or Google Analytics) and
no social-login SDK**, including Google Play Games sign-in.

## 12. Data we do not collect

We do not collect your real name, email address (except when you email us), phone number,
contacts, photos or videos, microphone audio, files, payment details, advertising ID, browsing
history or precise location, and there are no account passwords.

## 13. Children

Douzain is for players aged 13 and over. We do not knowingly collect personal data from children
under 13. If you believe a child under 13 has played online, email us with what you know. We will
look into it, and we may ask for more information. If we find that data we hold belongs to a child
under 13, we will delete it. We do not delete a player's data on an unsupported report alone.

## 14. Permissions the app asks for

| Permission | Why | Leaves the phone? |
|---|---|---|
| Internet | Online play (section 4), creature registry (5), gameplay statistics and crash reports if allowed (6, 7), downloading game content | Only the data in those sections |
| Camera | The Lens (section 1) | No |
| Approximate location (Android: coarse; iPhone: while using the app, Precise off) | Which creatures appear; the Observatory sky (section 2) | No |
| Notifications | Creature reminders (section 8) | No |
| Motion (iPhone) | Turning the view in the Lens by turning the phone | No |
| Vibrate | Haptic feedback | No |

## 15. Changes to this policy

When the game changes what it does with data, we update this page and the "Last updated" date
before the new version reaches players.

## 16. Contact

Questions or requests: **studio.douzain@gmail.com**.
