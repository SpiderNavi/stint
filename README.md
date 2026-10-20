# Stint

A tiny floating focus timer for Windows. Stint pairs a customizable Pomodoro countdown with an overtime stopwatch, so you can finish your thought without losing track of how long you have worked.

## Download and run

The Windows executable and source archive will be added to this repository.

No installer is needed. Download the executable and double-click it. The supplied build is unsigned, so Windows may display a SmartScreen warning. Review the source and only run software you trust.

## Features

- Movable, always-on-top floating timer with a compact pill view.
- Customizable focus periods, breaks, rounds, and periodic long breaks.
- Silent double-blink when a block ends.
- Overtime stopwatch after the countdown reaches zero.
- Total focused time and extra time counters.
- Optional automatic progression between blocks.
- System tray controls and a right-click menu.
- Embedded Inter fonts with tabular digits for a steady countdown.
- Remembers settings, window position, and compact-view preference.

The default plan is **20 minutes focus / 5 minutes break × 4 rounds**.

## How it works

A **session** is the complete plan. A **round** contains a focus block followed by a break; the final round has no trailing break. A **block** is a focus, break, or long-break segment. **Extra** is the time spent beyond a block's countdown.

Click the main round button to start or pause. When the countdown ends, the card blinks twice and begins counting overtime; click the check button to advance. With auto-continue enabled, Stint advances automatically instead.

Drag the card to reposition it. Hover to reveal skip, restart, setup, compact, and close controls. Double-click the card to toggle compact mode. Right-click the card or tray icon for additional controls.

## Windows Focus

Stint can open the Windows Focus settings page using `ms-settings:quiethours`. It does not automatically start or stop a Windows Focus session. Opening that page is optional and can be disabled in setup.

Settings are saved locally in `%APPDATA%\Stint\stint.ini`.

## Build from source

Stint is a native C++17 Win32 application rendered with GDI+. The included build script targets Windows x64 using MinGW-w64.

On Debian/Ubuntu or WSL, install the MinGW-w64 C++ compiler and binutils, then run:

```sh
sh build.sh
```

The script expects `x86_64-w64-mingw32-g++`, `x86_64-w64-mingw32-windres`, and `x86_64-w64-mingw32-strip`. It produces `Stint.exe` in the project root.

The prepared font files are already included, so Python is not required for an ordinary build. `prepfonts.py` is an optional font-preparation utility requiring FontTools and the original Inter Regular, SemiBold, and Inter Display Bold TTF files.

## Repository contents

| Path | Purpose |
| --- | --- |
| `stint.cpp` | Application source |
| `stint.rc`, `stint.manifest`, `stint.ico` | Windows resources, manifest, and icon |
| `build.sh` | MinGW-w64 build script |
| `prepfonts.py` | Inter subset and tabular-digit preparation |
| `fonts/` | Embedded font subsets and Inter license |
| `bin/Stint.exe` | Supplied Windows executable |
| `downloads/Stint-source.zip` | Original supplied source archive |

## Project background

Created by Navindu Karunarathna with AI-assisted development. The original idea was a small, silent timer that stays visible while working, supports flexible focus/break plans, and measures time spent continuing beyond the planned focus block. The interface was subsequently updated to use embedded Inter fonts.

The supplied development notes report testing under Wine rather than on a physical Windows machine. This repository upload preserves the supplied source and executable; it does not constitute a new Windows runtime test.

## Font license

Inter is distributed under the SIL Open Font License 1.1; see [fonts/Inter-LICENSE.txt](fonts/Inter-LICENSE.txt). No separate application-source license has been selected.
