<a id="readme-top"></a>

<!-- PROJECT SHIELDS -->
![C++](https://img.shields.io/badge/C%2B%2B-20-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)
![DirectX](https://img.shields.io/badge/DirectX-11-107C10?style=for-the-badge&logo=xbox&logoColor=white)
![FMOD](https://img.shields.io/badge/FMOD-000000?style=for-the-badge&logo=fmod&logoColor=white)
![Windows](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)
[![Apache 2.0 License][license-shield]][license-url]

<!-- PROJECT TITLE -->
<div align="center">
  <h1>Protogame2D</h1>
  <p>A minimal 2D game template built on the Daemon Engine for rapid prototyping</p>
</div>

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [How to Install](#how-to-install)
- [How to Use](#how-to-use)
- [Project Structure](#project-structure)
- [License](#license)
- [Contact](#contact)

## Overview

Protogame2D is a starter template for building 2D games on the custom [Daemon Engine](https://github.com/daemon-engine/DaemonEngine) ([documentation](https://daemonengine.dadavidtseng.com)). It provides a clean, minimal scaffold with an application lifecycle, a two-state game state machine (Attract → Game), an orthographic camera, event-driven state transitions with audio feedback, and built-in debug tools (FPS counter, pause, slow-mo, single-frame step).

Designed as a boilerplate that can be cloned and extended into a full game project. The V8 scripting subsystem is disabled by default via `EngineBuildPreferences.hpp` to keep the build lightweight; without it, the project needs neither V8 nor OpenSSL and builds for both x64 and x86.

## Features

- **Game state machine** — Event-driven Attract ↔ Game transitions with `OnGameStateChanged` callbacks and audio cues
- **2D orthographic rendering** — Screen-space camera with `VertexList_PCU` immediate-mode drawing (disc, line segments)
- **Debug tools** — Real-time FPS/time/scale HUD, pause (P), single-frame step (O), slow-mo at 0.1× (T hold), developer console (~)
- **Window management** — Windowed ↔ fullscreen toggle (R); the screen camera follows the new window size
- **Structured logging** — `DAEMON_LOG` macro with verbosity levels for lifecycle tracing

## How to Install

### Prerequisites

- Visual Studio 2022 or later with the C++ desktop development workload (the project uses the v143 toolset)
- Windows 10/11 (x64 or x86)
- DirectX 11 compatible GPU

### Build

The engine is included as the `Engine/` Git submodule, so clone recursively:

```bash
git clone --recursive https://github.com/daemon-engine/Protogame2D.git
```

If you already cloned without `--recursive`, fetch the engine with:

```bash
git submodule update --init
```

1. Open `Protogame2D/Protogame2D.sln` in Visual Studio
2. Choose a configuration: `Debug` or `Release`, `x64` or `x86`
3. Build the solution (the Engine project is referenced automatically)
4. The executable is deployed to `Protogame2D/Run/` via post-build event

## How to Use

### Controls

| Action | Key |
|--------|-----|
| Start game | Space |
| Return to attract / Quit | ESC |
| Toggle windowed / fullscreen | R |
| Restart game (in game) | F8 |

### Debug Controls

| Action | Key |
|--------|-----|
| Pause / Unpause | P |
| Step single frame | O |
| Slow-mo (0.1×) | T (hold) |
| Developer console | ~ |

### Running

Press F5 in Visual Studio; the project already starts the game with `Run/` as its working directory. To launch it directly, run `Protogame2D_<Configuration>_<Platform>.exe` (for example `Protogame2D_Debug_x64.exe`) from `Protogame2D/Run/` — the working directory must be `Run/` for asset loading.

## Project Structure

```
Protogame2D/                           # Repository root
├── Engine/                            # Daemon Engine (Git submodule)
├── Protogame2D/
│   ├── Code/Game/
│   │   ├── Framework/                 # Application framework
│   │   │   ├── Main_Windows.cpp       # WinMain entry point
│   │   │   ├── App                    # Application lifecycle (Startup → RunMainLoop → Shutdown)
│   │   │   └── GameCommon             # Global pointers, GAME_SAFE_RELEASE
│   │   ├── Gameplay/                  # Game logic
│   │   │   └── Game                   # State machine (Attract ↔ Game), rendering, time and window controls
│   │   └── EngineBuildPreferences.hpp # Engine feature toggles (V8 scripting disabled)
│   ├── Run/                           # Runtime directory
│   │   ├── Data/Audio/                # Sound effects (TestSound.mp3)
│   │   ├── Data/Config/               # Engine subsystem, log, and log rotation settings
│   │   ├── Data/Fonts/                # Bitmap font (DaemonFont)
│   │   └── Data/Shaders/              # HLSL shaders (Default)
│   └── Protogame2D.sln                # Visual Studio solution
├── LICENSE
└── README.md
```

## License

Copyright 2026 Yu-Wei Tseng

Licensed under the [Apache License, Version 2.0](LICENSE).

## Contact

**Yu-Wei Tseng**
- Portfolio: [dadavidtseng.com](https://dadavidtseng.com)
- GitHub: [@dadavidtseng](https://github.com/dadavidtseng)
- LinkedIn: [dadavidtseng](https://www.linkedin.com/in/dadavidtseng/)
- Email: dadavidtseng@gmail.com

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- REFERENCE-STYLE LINKS -->
[license-shield]: https://img.shields.io/github/license/daemon-engine/Protogame2D.svg?style=for-the-badge
[license-url]: https://github.com/daemon-engine/Protogame2D/blob/main/LICENSE
