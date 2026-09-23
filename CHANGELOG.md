# Changelog

All notable changes to this project are documented here.
Versions follow [Semantic Versioning](https://semver.org/).

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
