# Douzain — Privacy Policy

**Last updated:** 21 November 2026

Douzain ("the game", "we", "us") is a tactical creature game for Android and iPhone. It is made by
a private individual, a hobbyist, who publishes it under the name **Studio Douzain** and is the
person responsible for the data described here (the "controller"). Contact:
**studio.douzain@gmail.com**.

This policy describes what this version of the app actually does with data. It was written from
the app's code and from the settings of the server it talks to.

---

## Summary

- **No accounts.** There is no sign-up, no login, no password and no email address in the game.
  The game makes a player ID on your phone.
- **Your player name is made by the game.** It is picked from a fixed list of names; you can ask
  for a different one until you lock one in. You cannot type your own name.
- **No ads, no advertising or tracking SDKs, no social-login SDK, no in-app purchases.** We never
  sell data.
- **The camera** shows creatures through the Lens, live on your phone. No camera image is ever
  stored or sent.
- **Location** is read approximately, on your phone, to choose which creatures appear and to draw
  the sky. It never leaves your phone.
- **Some things reach our server even if you never play online:** each creature you capture is
  registered (with your player ID), the game asks how many of a species have been caught, and
  opening the Arena loads the challenge board (with your player ID). Once you have played online,
  the game also checks for waiting matches and your ladder standing when it opens (section 4).
- **Online play** sends your player ID, player name, avatar, Colours, moves and game standing to
  our own server (Hetzner, Finland). Your player name and standing (rating, ladder points,
  crowns) are **shown publicly** on the challenge board and the ranked ladder.
- **Creature registry entries are public**, including the player ID of the coin's owner (section
  5). Test builds use a test ledger that we will delete before public launch.
- **Gameplay statistics and crash reports are optional.** Neither is sent unless you tap Allow on
  the gameplay-data card, and you can change your mind at any time. Crash reports go to Sentry, a
  crash-reporting service (section 7).
- **You can ask us to delete your data** by email; see section 10.

---

## 1. Camera

The Lens uses your phone's camera to show creatures beyond the veil. The camera feed is drawn
straight to the screen. **No camera image is ever saved, recorded or uploaded.**

You can take an in-game snapshot in the Lens. It is saved on your phone only, and it can only be
taken when the view is fully in Serein: it is built from the game's own 3D picture, never from
the camera, so it cannot contain a real-world photo.

You can refuse the camera permission. The Lens then cannot show the world through your camera,
though some story scenes in the Lens still open on a plain background. Story mode, battles, the
collection and online play all work without it.

## 2. Location

**Permission:** approximate location only. On Android the app asks for coarse location; on iPhone
it asks for location while using the app, with Precise Location off by default. It never reads
location in the background.

**When it is read:** when you open the Lens or the Observatory, the app uses a recent position if
it already has one, or asks your phone once for an approximate position.

**What it is used for:** on your phone, the position is turned into broad tags (a region and a
climate band) with a lookup table built into the app; no map or geocoding service is called. The
tags make some creatures more or less likely to appear. The position is also used to work out the
sky, in the Lens and in the Observatory.

**Does it leave the phone?** No. The position is held in memory only and is never saved.
Gameplay statistics strip any location field, and the position is not put into creature
registrations or online matches. The species you catch are sent when a creature is registered
(section 5), and because creatures are chosen partly by region, which species you catch can
loosely reflect where you play.

You can refuse the location permission. The Lens still works. If you don't share your location,
the game picks a random place on Earth as your home for which creatures appear; it is stored only
on your phone and never sent.

## 3. Your player ID, device key and player name

- **Player ID.** On first launch the app makes an ID on your phone from the time it was made and a
  random number, so anyone who sees your player ID could work out roughly when you first opened
  the game. Settings → ACCOUNT shows a short code made from it (it starts with `DZ-`). The player
  ID does not come from your phone's hardware or your Google or Apple account. Our server uses it
  to keep your online matches, challenge-board postings and creature registrations together, so
  it is linked to those records of your play.
- **Device key and ranked ID.** The first time you play online (start or join a match, use the
  challenge board, or search for a ladder match) the app makes a signing key on your phone. The
  key has a private half and a public half. The private half never leaves your phone. The public
  half is sent with your online matches and challenge-board actions, so the server can check that
  results really came from your phone. A **ranked ID**, a scrambled code worked out from the public
  half, is used to look up your ladder standing and is shown on the public ladder. Neither half
  comes from your phone's hardware or your Google or Apple account.
- **Player name.** The game gives you a name from a fixed list of names. You can ask for a new
  one until you like it, then lock it in. Names are one word of up to eight letters. Because you
  cannot type a name, the game does not collect a name you wrote.

## 4. Online play, and the checks the game makes in the background

**Checks the game makes without you starting anything:**
- **Waiting matches.** While your phone holds an online match or a challenge-board posting (or a
  record of one you hid), the game asks our server whether any of your matches are waiting for
  your move: when the game opens, when you come back to it, when you open the main menu, the Arena
  or your matches list, and from time to time while those screens are open. This sends your
  player ID. A phone that has never played online does not make this check.
- **Ladder standing.** If you have locked in a name and played online, or have a ranked result
  waiting to be sent, then when the game opens and when you come back to it (at most once every 5
  minutes for this check) it fetches the ranked ladder and looks up your standing with your ranked
  ID. Any ranked results not yet delivered are sent at the same time. Opening the ladder screen or
  the Arena's ladder board fetches the ladder too; the standing lookup there is made only if your
  phone already has a device key.
- **Challenge board.** Opening the Arena loads the challenge board from our server, even if you
  have never played online. This sends your player ID, so the board can mark your own postings,
  and the game's version, so it only lists challenges your game can accept.
- **Account screen.** Opening Settings → ACCOUNT asks our server whether accounts are available.
  This sends nothing about you.

Like every request, these reach our server with your IP address (see "IP addresses" below and
"Server logs" in section 10).

**When you play online.** If you start or join an online match, use the challenge board or play
ranked, your phone also sends the match data below.

The server is a program we run on a server rented from **Hetzner Online GmbH in Helsinki,
Finland**. Cloudflare provides only our domain name (DNS) and holds no game data; traffic goes
straight to our server, not through Cloudflare. The game's requests to our server are encrypted
(HTTPS).

**What is sent:** your player ID, your player name, your avatar and Colours (each picked from a
fixed list in the game, never a photo), your moves, army and match clock, the match's invite code
(random letters), the public half of your device key, and technical details such as the game
version and the match's settings. For ranked play, the app also sends your signed result. Online
play has no chat and no other free-text field.

**Who can see it:**
- Your opponent sees your player name, avatar, Colours and moves, whether you are connected and
  when you were last seen. If you join someone's match, their game also receives your player ID.
- **Anyone** who has a match's invite code can see that match's status: whether it is waiting, in
  play or over, when it started and was last active, and whether each player is connected.
- **Everyone** who opens the challenge board sees your posting: your player name, rating, ladder
  points and crowns, and the stake and clock you chose. Your player ID is not shown there.
- **Everyone** can see the ranked ladder: your locked player name, ranked ID, rating, points,
  crowns, wins and losses, and, for a single player's standing, draws and the dates and match codes
  of crowns won. You appear on the ladder only once you have locked in a name and played ranked.
- **Anyone who knows a player ID** can see that player's list of matches waiting for a move (the
  match codes, whose turn it is and when each last changed). Because the creature registry shows
  player IDs publicly (section 5), please treat your player ID as public.

**How long it is kept:**
- A live match ends as abandoned after 10 minutes with no activity from either player, and a
  play-by-mail match after 90 days; some matches end sooner, for example when a turn clock runs
  out. After a match ends, it is deleted 7 days after the last time either player's game opened
  it (a ranked match: 7 days after it ended). A match a player closes is deleted within a minute.
- An invite nobody joins is deleted after about 2 hours (live) or about 3 days (play-by-mail).
- The list of your matches that are waiting for your move is deleted 60 days after it last
  changed, by a daily clean-up.
- A challenge-board posting stays up until you withdraw it, someone accepts it, or it expires
  after 30 days; an expired posting is deleted by a daily clean-up a day later.
- Ranked results (wins, losses, rating, points, crowns and the match codes and times behind them)
  are kept so that everyone's ladder stays correct. They have no fixed end date. If you ask us to
  delete your data, we remove your name and player ID from them and replace your key with a new
  random one (section 10).

**IP addresses:** the server uses your IP address to limit abuse (a cap on requests in a given
time). Most of these limits live only in the server's memory. Three are written to the server's
database:
- **Quick match.** While you are in the quick-match queue, your entry holds your player ID, your
  match choices and a scrambled form of your IP address (made with a secret value that changes
  whenever the server restarts). An entry stops being matched after 5 minutes. It is removed from
  the database the next time the queue is used after that, so while few people play it can stay
  longer.
- **Challenge postings.** A friendly challenge posting (or a ladder posting the game could not
  sign) stores a scrambled form of your IP address, made the same way, next to your player ID. It
  is deleted with the posting.
- **Creature registrations.** The limit on registrations stores your IP address (for IPv6, the
  first half of it) with the time of each registration, in a log kept for each species. It is not
  stored with your player ID. An entry older than 5 minutes is removed the next time a creature of
  the same species is registered, so while there are few players it can stay much longer.

A backup taken while any of these is stored keeps it for that backup's life (section 10).

## 5. Creature registry ("the Great Ledger")

When you capture a creature, in the Lens or in story mode, the app registers it with our server so
that it gets a serial number. The registration is sent about a day after the capture, or the next
time you open the game after that; you can also register a coin straight away at the Pyx. This
happens whether or not you allow gameplay statistics, because the serial number is part of the
game. Some story-only creatures are not registered.

When you capture a creature in the Lens, the app also asks our server how many of that species
have been caught before, so it can tell you if yours is the first. That question sends only the
species name (and, like every request, your IP address).

**Test builds use a test ledger.** Serial numbers in test builds are not permanent: we will delete
the whole test ledger before the game's public launch, and a new ledger starts then.

**What is sent:** the coin's ID, the species, the capture time, the app's build ID, the creature's
model version and your player ID. No player name and no location.

**What is kept:** the above, plus the serial number, edition, the order in which it was
registered, the registration time, and a tamper-evident signature where that is switched on. To
limit abuse, the server also keeps a short log of registration times by player ID (and by IP
address, section 4).

**Who can read it:** registry entries are public. Anyone who knows a coin's ID can read its
serial, edition, species, capture and registration times, signature and the owner's player ID;
anyone who knows a player ID can list that player's registered coins. A public list shows the
first coin registered of each species, with the species and the time. The registry also has a
name field, and both the coin lookups and the first-coins list show it if a name is stored; this
version of the game never sends a name with a registration. The registry never holds your
location.

**How long:** kept until we delete the test ledger. **If you ask us to delete your data sooner,
we remove your player ID and any name from your entries.** The coin's ID, serial number, species,
times, edition and signature remain, but no longer show your player ID.

## 6. Gameplay statistics (optional, off unless you allow it)

The first time you play, a card asks: *"May we collect gameplay data to make Douzain better?"*,
with **Allow gameplay data** and **No thanks**. No statistics are sent before you answer, and
none are sent if you choose No thanks. You can change your choice at any time in Settings →
ABOUT.

**If you allow it, the app sends:**
- play sessions (the first launch after you allow it, app opened and closed, session number and
  length, the screen a session ended on);
- progress and results (for example captures, with the species and whether it was new; story
  stages started or finished; Arena matches started or finished, with the opponent's level, damage
  dealt and rounds played; and a snapshot of your collection size, story progress, in-game coin
  balance and your match rating rounded to the nearest 100);
- in-game spending and earning of the game's own currency (what you bought with it; there is no
  real money in the game);
- the app version and build ID, and a short technical note of which save formats are on the
  phone;
- a random ID made on your phone for statistics only. It is a different value from your player
  ID and ranked ID, and we do not join the statistics with your player ID, name or location.

**Where it goes:** to our own server (the same Hetzner server, a separate database). Your IP
address is used only in memory, to limit abuse; it is not stored with the statistics. Times are
stored to the day only.

**How long:** deleted automatically after **180 days**. We also keep daily totals (counts, not
individual records) to run the service.

**Stopping and deleting:** turning sharing off in Settings → ABOUT stops new statistics at once
and deletes any not yet sent from your phone; anything already on its way may still arrive.
**Delete my analytics data** (Settings → ABOUT) asks our server to erase everything tied to your
statistics ID; if your phone is offline, the request is sent the next time it can reach our
server. Afterwards the server keeps only that ID and the date of the request on a do-not-accept
list, so late-arriving statistics are refused, until the 180-day limit passes.

## 7. Crash reports (optional, same choice)

Crash reports start only if you tap **Allow gameplay data** on the card in section 6; if you
choose No thanks, no crash reports are sent. They go to **Sentry** (Functional Software, Inc.), a
crash-reporting service, and are stored in Sentry's **European Union** region for **30 days**.

While gameplay data is allowed, Sentry also receives a small "session" note each time the game
opens, so we can see what share of play sessions crash: a random session ID, when the session
started and ended, whether it ended in an error, the app version, and the browser and phone
description the app runs with. It holds no player ID, name or location.

A crash report holds the error and where it happened in the code, the app version, the phone
model, operating-system version and language, and a short trail of recent app events (such as
screens opened, buttons tapped and server addresses called). Sentry is set not to store IP
addresses. Before a report is sent, the app removes cookies, user details and query strings, cuts
the variable parts out of server addresses, and removes text shaped like a player ID, coin ID or
other long ID from the error message and the trail of events. This filter works by pattern, so it
may not catch everything. The game does not put your player name or location into crash reports
on purpose.

If you turn sharing off, crash reporting stops; a report already being sent may still arrive.

## 8. Notifications

If you allow notifications, the app may remind you, a few hours after you close the Lens, that a
creature you have not caught yet is nearby or that something new has appeared. These reminders
are worked out and scheduled on your phone from your last visit to the Lens; nothing is pushed
from a server, and nothing about where you are is tracked or sent. On Android the app may also
restore a scheduled reminder after your phone restarts. You can turn reminders off in Settings →
NOTIFICATIONS or in your phone's settings.

## 9. Data on your phone, sharing, and phone backups

Your collection, progress, settings, player ID, device key, player name, statistics ID, your
gameplay-data choice and the details the game needs to resume your online matches are stored on
your phone. Uninstalling the app deletes them from the phone (but not from a phone backup, below).

**Sharing is your choice.** Some things open your phone's share sheet: an invite code for a
friend, a print, or a keepsake book. Whatever you share goes only to the app or person you pick
there, and is then handled under their settings and terms; it does not pass through our server,
and nothing is sent if you close the share sheet. On iPhone, saving a print to your photo library
uses the add-only Photos permission (section 14); the app cannot read your photos.

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

**What we delete from our server:** your player name and player ID, your online matches, your
list of matches waiting for a move, your quick-match queue entry, your challenge-board postings
and any challenge you were holding. Matches you were in are deleted whole, including your
opponent's copy on our server, even a match still in play. A challenge you accepted stays on the
board's records as accepted, but no longer points to you.

**What we keep after a deletion:**
- Creature registry entries: the coin's ID, serial number, species, times, edition and signature,
  with your player ID and any name removed (section 5).
- Ranked results: wins, losses, rating, points, crowns, and the match codes and times behind them,
  with your name and player ID removed and your key replaced by a new random one, so your
  opponents' records stay correct. The ladder row stays, without your name.

**What a deletion request does not cover:**
- Gameplay statistics: they are not linked to your player ID, so use **Delete my analytics data**
  in the game (section 6), or they go after 180 days.
- Crash reports at Sentry: they go after 30 days.
- The IP address log for creature registrations (section 4), which is not stored with your player
  ID and is cleared as described there.
- Server logs and backups, which expire as shown below.
- Copies on phones: your own phone and its backups (section 9), and any copy of a match or
  message on another player's phone.
- Our email exchange with you about the request.

**Retention at a glance:**

| Data | Kept for |
|---|---|
| Live / play-by-mail match | until it ends (10 minutes / 90 days with no activity, or sooner), then 7 days after either player last opened it (ranked: 7 days after it ended); a match a player closes, about a minute |
| Unjoined invite | about 2 hours (live) / about 3 days (play-by-mail) |
| Matches-waiting-for-your-move list | 60 days after it last changed (daily clean-up) |
| Challenge-board posting (and, for an unsigned posting, a scrambled IP address) | until withdrawn or accepted, at most 30 days; deleted by a daily clean-up a day after it expires |
| Quick-match queue entry (player ID, match choices, scrambled IP address) | matched for up to 5 minutes; removed from the database the next time the queue is used after that |
| Ranked results | no fixed end; on request, name and player ID removed and key replaced |
| Creature registry entries | until we delete the test ledger before public launch; on request your player ID and any name are removed sooner |
| Creature registration limit (IP address and time) | removed when over 5 minutes old, at the next registration of the same species (section 4) |
| Gameplay statistics (if allowed) | 180 days, or sooner on Delete my analytics data |
| Crash reports (if allowed) | 30 days, at Sentry (EU region) |
| Server logs | 14 days |
| Server backups | nightly copies on the server for 14 days; encrypted off-site copies (Hetzner, EU) kept daily for 14 days, weekly for 8 weeks and monthly for 3 months; copies taken before server updates deleted after 90 days |

**Backups:** because of the backups above, data deleted from our server is gone from all of our
server's backups within about six months.

**Server logs:** our server's logs can contain an IP address, a player ID, a ranked ID or an
invite code, for example from the background checks in section 4. They are deleted automatically
after 14 days.

Your other rights, and how to complain, are in section 16.

## 11. Other companies involved

- **Hetzner Online GmbH** (Germany; server in Finland) runs the server our relay and database are
  on, under a data processing agreement. Off-site backups are stored with Hetzner, encrypted.
- **Sentry / Functional Software, Inc.** (a US company) receives crash reports if you allow them
  (section 7), under a data processing agreement; they are stored in its EU region, and any
  access from outside the UK and EU is covered by the transfer terms in that agreement.
- **Google** (Android) delivers the game's extra content through Play Asset Delivery, when you
  install the game and, if needed, after it starts, and runs Android's backup (section 9). Google
  does this under its own terms.
- **Apple** (iPhone) distributes the app through the App Store and TestFlight, delivers the
  game's extra content after install, and runs iCloud Backup (section 9), under Apple's terms. We
  do not use Game Center sign-in in this version.
- **Cloudflare** provides our domain name service (DNS) only; game data does not pass through or
  stay with Cloudflare.
- **GitHub** hosts this policy page. If you open it, GitHub sees your visit like any website
  does. The game sends GitHub nothing else.

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
| Internet | Online play and the background checks (section 4), creature registry (5), gameplay statistics and crash reports if allowed (6, 7), downloading game content | Only the data in those sections |
| Network state (Android) | Added by a code library the app includes; lets the app see whether you are online | No |
| Camera | The Lens (section 1) | No |
| Approximate location (Android: coarse; iPhone: while using the app, Precise off) | Which creatures appear; the sky (section 2) | No |
| Notifications | Creature reminders (section 8) | No |
| Run at startup and keep awake (Android) | Restoring scheduled reminders after a restart (section 8) | No |
| Add to Photos (iPhone) | Saving a print you choose to save (section 9); the app cannot read your photos | No |
| Motion (iPhone) | Turning the view in the Lens by turning the phone | No |
| Vibrate | Haptic feedback | No |

## 15. Why we use your data (legal bases)

UK and EU data protection law asks us to say which legal basis we rely on:
- **To run the game you asked for** (performance of a contract): online play, the challenge
  board, the ranked ladder and deletion requests.
- **Your consent:** gameplay statistics and crash reports (sections 6 and 7). You can withdraw it
  at any time in Settings → ABOUT; that does not affect what was sent before.
- **Our legitimate interests:** the background checks for waiting matches and ladder standing,
  and loading the challenge board when you open the Arena, so the game is up to date when you
  open it (section 4); the creature registry, so that each
  coin gets a unique serial number that can be checked (section 5); limiting abuse by IP address;
  and server logs and backups, to keep the server running and recover from faults. You can object
  to these (section 16).
- **Your phone's permissions:** the camera, location, notifications and photos permissions are
  used only on your phone, and only after you allow them.

## 16. Your rights, and complaints

You can ask us, at **studio.douzain@gmail.com**, for a copy of your data, to correct it, to delete
it (section 10), to restrict how we use it, to object to a use based on our legitimate interests,
or for a copy of data you gave us in a form you can take elsewhere. Include your Player ID if you
can, so we can find your records. We reply within one month. We do not make decisions about you
by automated means that have legal or similarly significant effects; ranked ratings are worked
out automatically from match results and the game's fair-play rules.

If you are unhappy with how we handle your data, you can complain to the UK Information
Commissioner's Office (ico.org.uk) or your local data protection authority.

## 17. Changes to this policy

When the game changes what it does with data, we update this page and the "Last updated" date
before the new version reaches players.

Sign-in with Apple or Google may be added later. It is not in the game today. If it is added, we
will first update this policy to say exactly what is shared, and tell players before anything
changes.

## 18. Contact

Questions or requests: **studio.douzain@gmail.com**. The person responsible for protecting your
personal information is the developer, at the same address.
