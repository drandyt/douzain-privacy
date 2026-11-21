# Douzain — Request deletion of your data

This page is for players of **Douzain**, a game by **Studio Douzain**, who want their data
deleted. Douzain has no accounts: no sign-up, no login and no email address in the game. What our
server holds about you is tied to a player ID made on your phone, and your player name is picked
by the game from a fixed list, never typed by you.

## How to ask us to delete your data

1. If you still have the game: open Douzain, open Settings, then ACCOUNT, and note your
   **Player ID**. It starts with `DZ-`.
2. Email **studio.douzain@gmail.com** from any address, with the subject **"Data deletion
   request"**. Include your Player ID if you have it, your player name, and roughly when you last
   played. Anything else you remember, such as an opponent's name or the date of a match, helps
   us find your records.
3. We reply to confirm and finish the deletion within **30 days** of your email.

You do not need the game to ask. If you have lost your phone, email us with whatever you remember.
The same steps are on [relay.douzain.com/account/delete](https://relay.douzain.com/account/delete).

## Delete your gameplay statistics yourself, in the game

If you allowed gameplay data, open Settings → ABOUT and tap **Delete my analytics data**. This
asks our server to erase everything tied to your phone's statistics ID; if your phone is offline,
the request is sent the next time it can reach our server. Afterwards the server keeps only that
ID and the date of the request, so late-arriving statistics are refused, until the 180-day limit
passes. Turning sharing off stops new statistics and deletes any not yet sent from your phone;
anything already on its way may still arrive.

## What we delete from our server

- Your player name and player ID.
- Your online matches, your list of matches waiting for your move, your quick-match queue entry,
  your challenge-board postings and any challenge you were holding. Matches you were in are
  deleted whole, including your opponent's copy on our server, even a match still in play. A
  challenge you accepted stays on the board's records as accepted, but no longer points to you.

## What we keep after a deletion

- **Creature registry ("Great Ledger") entries:** the coin's ID, serial number, species, times,
  edition and signature, with your player ID and any name removed. Test builds use a test ledger,
  which we will delete in full before the game's public launch.
- **Ranked results:** wins, losses, rating, points, crowns, and the match codes and times behind
  them, with your name and player ID removed and your key replaced by a new random one, so your
  opponents' records stay correct. The ladder row stays, without your name.

## What a deletion request does not cover

- **Gameplay statistics:** they are not linked to your player ID, so use **Delete my analytics
  data** in the game (above), or they go after 180 days.
- **Crash reports at Sentry:** they go after 30 days.
- **The IP address log for creature registrations,** which is not stored with your player ID and
  is cleared as shown below.
- **Server logs and backups,** which expire as shown below.
- **Copies on phones:** your own phone and its backups, and any copy of a match or message on
  another player's phone.
- **Our email exchange with you about the request.**

## How long data is kept

| Data | Kept for |
|---|---|
| Live / play-by-mail match | until it ends (10 minutes / 90 days with no activity, or sooner), then 7 days after either player last opened it (ranked: 7 days after it ended); a match a player closes, about a minute |
| Unjoined invite | about 2 hours (live) / about 3 days (play-by-mail) |
| Matches-waiting-for-your-move list | 60 days after it last changed (daily clean-up) |
| Challenge-board posting (and, for an unsigned posting, a scrambled IP address) | until withdrawn or accepted, at most 30 days; deleted by a daily clean-up a day after it expires |
| Quick-match queue entry (player ID, match choices, scrambled IP address) | matched for up to 5 minutes; removed from the database the next time the queue is used after that |
| Ranked results | no fixed end; on request, name and player ID removed and key replaced |
| Creature registry entries | until we delete the test ledger before public launch; on request your player ID and any name are removed sooner |
| Creature registration limit (IP address and time) | removed when over 5 minutes old, at the next registration of the same species |
| Gameplay statistics (only if you allowed them) | 180 days, or sooner with Delete my analytics data |
| Crash reports (only if you allowed gameplay data) | 30 days, at Sentry (EU region) |
| Server logs | 14 days. They can contain an IP address, a player ID, a ranked ID or an invite code |
| Server backups | nightly copies on the server for 14 days; encrypted off-site copies (Hetzner, EU) kept daily for 14 days, weekly for 8 weeks and monthly for 3 months; copies taken before server updates deleted after 90 days. Data deleted from our server is gone from all of our server's backups within about six months |
| Your phone's own backup | not held by us. If Android backup or iCloud Backup is on, a copy of the app's data may be in that backup; you can delete it there |
| Camera images and location | never leave your phone, so we hold none to delete |

Full details: [Douzain Privacy Policy](https://drandyt.github.io/douzain-privacy/), section 10.

_Last updated: 21 November 2026_
