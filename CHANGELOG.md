# Changelog

All notable changes to this project are documented here.
Versions follow [Semantic Versioning](https://semver.org/).

## [0.2.1] — 2026-09-26

### Fixed
- **Play Order works.** Clicking **Load** on the Play Order tab showed "Cannot set properties of
  null" and the order, Favorites and build panels never appeared. They now show once the playbook
  loads.
- **A clearer message when the game's own play sheet can't be read.** It used to say the tool needed
  a "one-time game index", which was never true for the downloaded app and hid the real problem.
  It now says what actually went wrong (for example, that the Mod Manager needs to be opened once so
  it rebuilds its cache). If you still see an error there, please send us the new message.

### Changed
- **Roster Trim reads your dynasty's skill groups.** Which skill group each cap slot means depends on
  the dynasty mod a dynasty runs under, and some mods re-order them. Roster Trim now works out which
  layout a save uses and says so above the list, so the ceiling it reports for each player's job is
  read from the right group.

[0.2.1]: https://github.com/sdmart3/open-field-toolkit-releases/releases/tag/v0.2.1

## [0.2.0] — 2026-09-26

### Added
- **Run the offense you want, not just the one your roster suggests.** Step 2 of the Doctrine
  Generator has an **Offensive scheme** list and a **Lean** slider. Pick Air Raid, Spread, Option,
  Pro Style or any of the game's other offensive schemes, and set how far it outweighs your roster:
  0% is the book your players suggest, 100% is the scheme alone, and in between keeps the run sets
  your backs are good at. The formations it keeps, the gameplan and the call sheet all follow it.
- The schemes are measured from the game's own scheme playbooks, not made up: Air Raid comes out
  about 21% run, Pro Style 42%, Option 51%. Each one is described by what it does more and less of
  than the average playbook.
- After deriving, you see the run share three ways (your roster, the scheme, the finished book) and
  which of your players fit the scheme or pull against it, which is useful for recruiting.
- **Play Order** and **Favorites** tabs: set the order your sets and plays appear on the play-call
  screen, and build your Favorites formation.

### Fixed
- **Coach suggestions no longer include plays that aren't in your gameplan.** Playbooks built by the
  tool were carrying hidden leftover rows that the game still offered as suggestions, sometimes over
  100 extra candidates in a single situation. Every playbook the tool builds, offense and defense,
  now comes out clean. To clean a book made with an earlier version, run
  **Gameplan & Audibles** on it again (offense) or rebuild it (defense).
- **Runs were being counted as passes.** Plays the tool could not identify by name were all treated
  as quick-game throws, including several hundred runs (slashes, split zone, veer and midline
  option) and many deep shots. The tool now uses the game's own play type for those, so run/pass
  mixes, formation picks and gameplans are more accurate.
- Pass-protecting guards and centres are now recognised, so a pass-blocking line no longer pushes
  a book toward the run.

[0.2.0]: https://github.com/sdmart3/open-field-toolkit-releases/releases/tag/v0.2.0

## [0.1.3] — 2026-09-23

### Fixed
- **The dynasty save could change itself mid-run, and the pages came out wrong.** Building a
  playbook in step 3 refreshed the lists, which reset the save dropdown to whichever dynasty sorts
  first. Step 4 then read that save while still using the team you had picked from the other one.
  Your choice is now kept, and step 4 refuses to run at all if the save or team no longer matches
  the doctrine you derived.
- **A doctrine you just made could not be chosen anywhere else.** Every "Doctrine book" dropdown
  was filled once when the app opened and never again — on Doctrine Fit, Depth Chart, Position
  Changes, Roster Trim and Playbook Rebuild alike — even though the generator said the new book was
  "now in every Doctrine book list". They refresh when you switch tabs, and straight after a derive.

### Changed
- **"Select formations" is a real picker.** It used to score your master and show you a read-only
  list of what it had chosen. Now every set has a checkbox, the sets it rejected are listed too
  (with what each would still add to the book), and the playbook is built from what is ticked.
  Special-teams formations stay ticked and locked, because a playbook without them will not load.

[0.1.3]: https://github.com/sdmart3/open-field-toolkit-releases/releases/tag/v0.1.3

## [0.1.2] — 2026-09-23

### Fixed
- **The Doctrine and Call Sheet are real `.html` files now.** They were being handed to the browser
  as blob downloads, which saved as a file called `blob` with no extension — and the Open buttons
  did nothing at all. Both pages are written to disk every time, with proper names, and the buttons
  open them in your browser.
- Pages go to `Documents\Open Field Toolkit` by default. The folder box in step 4 still overrides
  it; leaving it blank now means "use the default" rather than "don't save".
- A doctrine whose name already ends in "Doctrine" no longer produces
  `derived-doctrine-doctrine.html`.

[0.1.2]: https://github.com/sdmart3/open-field-toolkit-releases/releases/tag/v0.1.2

## [0.1.1] — 2026-09-23

### Changed
- **No runtime prerequisite.** The app window is now published self-contained, so the .NET 8
  Desktop Runtime is no longer needed. The only remaining dependency is the WebView2 runtime, which
  ships with Windows 10 and 11. The download is larger as a result — 116 MB, up from 58 MB.

### Fixed
- `START TOOL.bat` checks for the WebView2 runtime and opens the toolkit in your browser if it is
  missing. Previously a missing runtime left you at an error dialog with nothing happening
  afterwards, even though the tool underneath works perfectly without it.
- Console output is plain ASCII; an em-dash was being mangled in the command window.

[0.1.1]: https://github.com/sdmart3/open-field-toolkit-releases/releases/tag/v0.1.1

## [0.1.0] — 2026-09-23

First public release.

### Added
- **Doctrine Generator** — derives a doctrine from a dynasty save and writes the Doctrine and Call
  Sheet pages. Explains itself: when a starter is 8+ Overall below someone passed over, the page
  gives the exact reason.
- **Build playbooks from the game's own** — every school's offense and every defensive scheme (199
  in total) can be rebuilt as a custom playbook, whole or cut down to your doctrine. Previously a
  custom book could only ever be a trimmed copy of one you already owned.
- **Doctrine Fit, Depth Chart, Position Changes, Roster Trim** — roster analysis against the roles
  your scheme actually needs, rather than raw Overall.
- **Playbook Rebuild** — trims a playbook and writes its gameplan and audibles. Backs up, builds to
  a temporary file, re-opens and verifies it, and only then replaces the original.
- **Mod Stack** — reports what each mod in your load order changes, per mechanism, and which mod
  wins each conflict.

### Notes
- Mod Stack needs a one-time index built from your own game installation. It detects when that is
  missing and says so rather than failing part-way through; every other tab works without it.
- The app is not code-signed, so SmartScreen will warn on first run.

[0.1.0]: https://github.com/sdmart3/open-field-toolkit-releases/releases/tag/v0.1.0
