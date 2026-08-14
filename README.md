# Rampage - Through Time  Recompiled

<!-- retcomm-readme-metrics -->
[![GitHub downloads (all assets, all releases)](https://img.shields.io/github/downloads/TechnicallyComputers/Rampage-Through-Time-Recomp/total)](https://github.com/TechnicallyComputers/Rampage-Through-Time-Recomp/releases)
[![GitHub downloads (latest release)](https://img.shields.io/github/downloads/TechnicallyComputers/Rampage-Through-Time-Recomp/latest/total)](https://github.com/TechnicallyComputers/Rampage-Through-Time-Recomp/releases/latest)
[![GitHub release](https://img.shields.io/github/v/release/TechnicallyComputers/Rampage-Through-Time-Recomp)](https://github.com/TechnicallyComputers/Rampage-Through-Time-Recomp/releases/latest)
<!-- /retcomm-readme-metrics -->

Static recompilation of **Rampage - Through Time** built on
[psxrecomp](https://github.com/mstan/psxrecomp) and
[recomp-ui](https://github.com/mstan/recomp-ui).

Rampage is a series of video games released by Midway for various consoles. The basic premise of the series is that the player controls a human transformed into a giant monster by a lab accident. The gameplay revolves around using your monster to destroy cities around the world while attacking or avoiding military forces. Rampage Through Time is the fourth game in the Rampage series. It was released on June 9, 2000. Its predecessor is Rampage 2: Universal Tour and it is followed by Rampage: Total Destruction. In the game, 7 previous Scumlabs monsters, plus a new one, use a time machine to rampage through time. The world is again rebuilding after the events of Universal Tour. To clean up the mess quicker, Scumlabs invent a time machine to send people back in time to fix the mess without having to do it in the present. Unfortunately, the monsters, who have somehow made it back to Earth, appear and run into the machine. They begin terrorizing the past, present, and future, messing up the time stream.

| | |
|---|---|
| Players | 3 |
| Region | USA |
| Publisher | Midway |
| Year | 2000 |

Scaffolded with the New Project Layout. See
`psxrecomp/docs/GAME_PROJECT_SETUP.md` for the full flow.

<!-- retcomm-readme-launcher -->
## RetComM Launcher

You can run this title **standalone** (release zip + the built-in recomp-ui
Generate & Build flow), or manage installs, updates, ROM/BIOS wiring, and queued
builds more intuitively with
**[RetComM Launcher](https://github.com/TechnicallyComputers/RetComM-Launcher)** —
the Retro Compilation Manager hub for self-compiling recomps.

[Downloads](https://github.com/TechnicallyComputers/RetComM-Launcher/releases) ·
[Full README & features](https://github.com/TechnicallyComputers/RetComM-Launcher#readme)

<p align="center">
  <img src="https://raw.githubusercontent.com/TechnicallyComputers/RetComM-Launcher/main/docs/screenshots/hub-and-game-launcher.png" alt="RetComM hub with a background build, next to a title’s recomp-ui launcher" width="720">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/TechnicallyComputers/RetComM-Launcher/main/docs/screenshots/queue-and-background-build.png" alt="Background cmake build with titles queued" width="720">
</p>

RetComM checks for updates, rebuilds with existing build data when possible,
shares the portable toolchain used by per-title launchers, and automates
BIOS/ROM/save plumbing so you are not stuck repeating each game’s wizard by hand.
<!-- /retcomm-readme-launcher -->

## Legal

You must own the original game. Disc images under `disc/` are gitignored and
must never be committed. Retail BIOS dumps are not redistributed; OpenBIOS is
used for Generate unless you supply your own SCPH locally.

Optional box art under `launcher_assets/img/` may come from
[libretro-thumbnails](https://github.com/libretro-thumbnails/libretro-thumbnails)
(`Named_Boxarts`); see `BOXART_SOURCE.txt` when present.

## Quick start (dev)

```bash
git submodule update --init --recursive
./psxrecomp/tools/ci/build_emitters.sh
python3 psxrecomp/psxrecomp_cli.py generate \
  --config game.toml --project-root . --disc disc/<your>.cue
cmake -S . -B build-release -G Ninja -DCMAKE_BUILD_TYPE=Release
cmake --build build-release --target psx-runtime
```

Zip prefix for CI artifacts: `rtt`.

## Symbols

Progressive map: `symbols.toml` → `python3 tools/sync_symbols.py` →
`psx_symbols.h` (`PSX_FN_*`). See `psxrecomp/docs/SYMBOLS.md`.

## Framework pins

Submodule gitlinks (`psxrecomp`, optional `recomp-ui`, nested `recomp-net`)
are authoritative. `framework_pins.txt` is an optional scaffold snapshot;
release CI logs SHAs with `record_pins.sh` but builds whatever the gitlinks
resolve to. Bump submodules deliberately — do not float on `main`/`master`
in release CI.

<!-- retcomm-readme-raid -->
---

<p align="center">
  <sub><b>R.A.I.D. — Retro AI Development</b> · a Discord for AI-assisted retro reverse-engineering, decomp &amp; recomp</sub>
</p>

<p align="center">
  <a href="https://discord.gg/Ad9BwSzctP"><img src=".github/raid-discord.png" alt="Join the Retro AI Development (R.A.I.D.) Discord" width="200"></a>
</p>
<!-- /retcomm-readme-raid -->
