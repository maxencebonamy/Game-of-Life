# Game-of-Life

An interactive implementation of Conway's Game of Life.

Draw a starting pattern on the grid with the mouse, then start the simulation with the space bar. The application is a desktop window built with Python and Pygame.

## Table of contents

- [Game-of-Life](#game-of-life)
	- [Table of contents](#table-of-contents)
	- [How it works](#how-it-works)
	- [Tech stack](#tech-stack)
	- [Repository structure](#repository-structure)
	- [Prerequisites](#prerequisites)
	- [Installation](#installation)
	- [Configuration](#configuration)
	- [Running locally](#running-locally)
	- [License](#license)

## How it works

1. **Drawing**: while the simulation is paused, a left click toggles the cell under the cursor. Dragging with the button held applies the same state (alive or dead) to every cell crossed.
2. **Start and pause**: the space bar starts or pauses the simulation. The window title shows `IDLE` or `RUNNING`. Drawing is disabled while the simulation runs.
3. **Generations**: a new generation is computed about every 0.1 second (`SPEED * FPS` frames at `FPS` frames per second). A living cell with 2 or 3 living neighbours survives, and a dead cell with exactly 3 living neighbours becomes alive.
4. **Grid size**: the grid covers the window plus `PADDING` hidden cells on each side. The outermost ring of cells is never updated.

## Tech stack

| Layer | Technologies |
| --- | --- |
| Language | Python 3 |
| Rendering and input | Pygame |

## Repository structure

```
.
├── assets/
│   └── icon.png     Window icon
├── script/
│   └── grid.py      Grid state, rendering and generation update
├── LICENSE          MIT license
├── config.py        Window, grid, color and speed constants
└── main.py          Window creation and main loop (events, update, display)
```

`config.py` imports `pygame` and `Vector2`, and every other module imports it with `from config import *`.

## Prerequisites

- [Python](https://www.python.org/) 3 (developed with 3.9)
- [Pygame](https://www.pygame.org/) (`pip install pygame`)

The repository does not declare a Python or Pygame version.

## Installation

```bash
git clone git@github.com:maxencebonamy/Game-of-Life.git
cd Game-of-Life
pip install pygame
```

## Configuration

All settings are constants in `config.py`. Edit the file and restart the application.

| Variable | Description | Example |
| --- | --- | --- |
| `WINDOW_SIZE` | Window dimensions in pixels | `Vector2(1280-2, 640-32)` |
| `WINDOW_COLOR` | Window background color | `(30, 30, 30)` |
| `GRID_COLOR` | Color of the grid lines and of dead cells | `(30, 30, 30)` |
| `PADDING` | Number of hidden cells on each side of the window (required) | `Vector2(5)` |
| `CELL_COLOR` | Color of living cells | `(255, 255, 255)` |
| `CELL_SIZE` | Cell size in pixels | `40` |
| `START_KEY` | Key that starts or pauses the simulation | `pygame.K_SPACE` |
| `FPS` | Number of frames displayed per second | `60` |
| `SPEED` | Animation speed factor: a generation is computed every `SPEED * FPS` frames | `0.1` |

## Running locally

Run the commands from the repository root, since the icon is loaded with a relative path.

```bash
python main.py
```

Controls:

- Left click or drag: toggle cells (paused only)
- Space bar: start or pause the simulation

## License

This project is licensed under the [MIT License](LICENSE).
