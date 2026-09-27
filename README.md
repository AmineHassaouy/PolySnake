# PolySnake 🐍

A playful twist on the classic Snake game: draw your own food points, and the snake  
fits a **polynomial curve** through them and glides along it — with classic  
grow-on-eat mechanics and **no teleporting** (screen wrap only at the edges).

Built with Python, [pygame](https://www.pygame.org/) and [NumPy](https://numpy.org/)  
in a single Jupyter notebook (`snake.ipynb`).

## ✨ Features

- **Click-to-draw food points** — place points anywhere on the canvas with the mouse.
- **Polynomial path fitting** — the snake fits a smooth polynomial (default degree 3)  
through your points using `np.polyfit`, plus a short linear approach segment  
from the head to the start of the curve.
- **Classic growth** — eating a point grows the snake by 10 segments.
- **No teleporting** — the snake moves smoothly at a constant speed  
(1 path step per frame at 60 FPS); positions only wrap around the screen edges.
- **Live path preview** — the full computed path is drawn while the snake follows it.
- **Instant reset** — press `R` to restore the starting state.

## 🎮 Controls


| Input           | Action                                           |
| --------------- | ------------------------------------------------ |
| **Left click**  | Add a food point                                 |
| **Right click** | Fit polynomial and send the snake along the path |
| **R**           | Reset snake, points, and path                    |


## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- pygame
- numpy
- Jupyter Notebook or JupyterLab (or VS Code with the Jupyter extension)

### Installation

```bash
git clone https://github.com/your-username/polysnake.git
cd polysnake
pip install pygame numpy jupyter
```

### Run

Open the notebook and run all cells:

```bash
jupyter notebook snake.ipynb
```

> Tip: run the cell with the game loop in Jupyter, or convert to a plain script with  
> `jupyter nbconvert --to script snake.ipynb` and run `python snake.py`.

## 🕹️ How It Works

1. **Add points** — each left click appends a point to the list.
2. **Right click** — the game:
  - Fits a polynomial of degree `min(3, points - 1)` through the points.
  - Prepends a 60-step linear segment from the snake's head to the curve's start.
3. **Follow** — the head advances one path step per frame; eaten points  
 (within `EAT_RADIUS = 18` px) grow the snake by `SEGMENTS_PER_FOOD = 10`.
4. **Finish** — when the path is exhausted, the snake stops and waits for your next path.

## ⚙️ Configuration

Tune these constants at the top of the notebook:


| Constant            | Default   | Meaning                            |
| ------------------- | --------- | ---------------------------------- |
| `WIDTH, HEIGHT`     | 800 × 600 | Window size                        |
| `degree`            | 3         | Polynomial degree for path fitting |
| `EAT_RADIUS`        | 18        | Eating distance from a point (px)  |
| `SEGMENTS_PER_FOOD` | 10        | Segments gained per food eaten     |


## 📁 Project Structure

```text
polysnake/
├── snake.ipynb   # The whole game in one notebook
└── README.md
```