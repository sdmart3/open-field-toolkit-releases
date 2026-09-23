# Open Field Toolkit

A Windows app for **EA Sports College Football 27** dynasty players. It reads your save and answers
scheme questions about it: what kind of team your roster actually is, who should be playing where,
and what a playbook built for them should contain.

It reads your own files, on your own machine. Nothing is uploaded anywhere.

**[Download the latest release](https://github.com/sdmart3/open-field-toolkit-releases/releases/latest)**

---

## Install

1. Download `OpenFieldToolkit-vX.Y.Z-win-x64.zip` from the releases page.
2. Unzip it anywhere — Desktop, Downloads, a USB stick. It does not install anything.
3. Run **`START TOOL.bat`**.

Windows SmartScreen will warn you on first run, because the app is not code-signed.
*More info → Run anyway.*

### Requirements

- Windows 10 or 11 (64-bit)
- [.NET 8 Desktop Runtime](https://dotnet.microsoft.com/download/dotnet/8.0) — for the window
- Microsoft Edge WebView2 Runtime — already present on Windows 11

If either is missing, run `bin\toolkit-server.exe` instead. It serves the same interface at
`http://localhost:7735`; keep the console window open while you use it.

---

## What it does

| | |
|---|---|
| **Doctrine Generator** | Works out what your team actually is, then writes two pages to keep open while you play: the **Doctrine** (who plays what, and why) and the **Call Sheet** (what to call, by situation). It also builds playbooks — either cut down one of your own, or rebuild any of the game's own 199 playbooks as a custom book. |
| **Doctrine Fit** | Ranks your roster, recruiting board, the whole recruiting class and the transfer portal against what your scheme actually asks for. |
| **Depth Chart** | Orders the depth chart by role fit rather than raw Overall. |
| **Position Changes** | Solves the whole lineup at once and says who should move where. |
| **Roster Trim** | Who to encourage to leave, ranked by how little the roster loses. |
| **Playbook Rebuild** | Trims a playbook to chosen formations, then writes its gameplan and audibles. |
| **Mod Stack** | Reports what your mod stack actually changes and which mod wins each conflict. Needs one-time setup — see below. |

### Is it safe for my save?

Reading is always safe. Only three things ever write — Depth Chart → Apply, Playbook Rebuild, and
Gameplan & Audibles — and each one asks first and makes a backup before touching anything.
**Close the game before using any of them.**

### About Mod Stack

Every other tab works the moment you open it. Mod Stack has to compare a mod against the *unmodded*
game, which needs an index built from your own installation — hundreds of megabytes, far too large
to ship. Until you build it, the tab says so and names what is missing. Nothing else is affected,
and you can ignore it entirely if you do not use gameplay mods.

### About playbooks

Playbook names must be **letters and numbers only**. That is the game's own rule, not this tool's —
a name with a space or a hyphen makes the game blank its Playbook and Audibles screens. It is also
the name the game displays, so the filename is what you will see in-game.

After building any playbook, run **Gameplan & Audibles** on it before you play.

---

## Verifying your download

Each release includes a `.sha256` file. To check the zip you downloaded matches:

```powershell
Get-FileHash .\OpenFieldToolkit-v0.1.0-win-x64.zip -Algorithm SHA256
```

Compare the result against the published checksum.

---

## Reporting a problem

Open an [issue](https://github.com/sdmart3/open-field-toolkit-releases/issues). Helpful to include:
the version, which tab, what you expected, and what happened. If a tab showed an error message,
paste it — they are written to say what actually went wrong.

## About this repository

This repo holds **releases only**. The source is maintained privately.

## Use and redistribution

Free to download and use. This is not open-source software and no licence to redistribute or modify
it is granted. It includes third-party components under their own licences, and it reads game data
formats belonging to their respective owners. Not affiliated with or endorsed by EA.
