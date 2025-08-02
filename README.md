# American Path Quest

## Challenge Description

Build an interactive browser-based game where the player must find a valid path on a square grid from a start point to an end point, following specific rules.

### Game Grid

- Grid is a square (e.g., 12x12 to 20x20) built from a 2D JavaScript array.
- Each cell has a type:
  - 0: Free path (white)
  - 1: Obstacle (black)
  - 2: Start (green)
  - 3: End (red)

### Gameplay Rules

- The player clicks on adjacent valid cells to build a path from green to red.
- The path is highlighted in blue.
- A valid path must:
  - Start at the green cell (2)
  - End at the red cell (3)
  - Only use valid cells (0, 2, 3)
  - Not repeat any cell
  - Avoid obstacles (1)
  - Be adjacent (no diagonal moves)

---

## Input/Output

**Input:** Predefined 2D JavaScript arrays per difficulty level (Beginner 12x12, Intermediate 15x15, Expert 18x18, Master 20x20). Loaded via UI buttons.

**Output:** 
- Interactive grid display with color-coded cells
- Stats: Level, Move Count, Hints Remaining, Score
- Action buttons: Reset, Hint, Check
- Visual feedback on path building and validation
- Achievements: e.g., First Path, Speed Runner

---

## Our Solution

### HTML (3.html)
Defines UI: game header, difficulty buttons, path stats (score, moves, hints), interactive grid container, control buttons, and achievement display.

### CSS (style.css)
- American patriotic theme with red, white, blue colors
- Stars and stripes background
- Grid cell styles:
  - .free: white
  - .obstacle: black
  - .start: green
  - .end: red
  - .path: blue
- Animations: cell pulse, hint glow, badge fade-in

### JavaScript (script.js)

#### Initialization
- Loads Beginner level (12x12 array)
- Builds grid from array
- Sets game variables (moves = 0, hints = 3, score = 0)
- Enables path clicking from start

#### Core Mechanics

- `buildGrid()`: Converts 2D array into DOM grid cells
- `handleCellClick()`: Adds cell to path if adjacent, valid, and not already selected
- `checkPath()`: Verifies path rules:
  - Starts and ends correctly
  - No repeated cells
  - All adjacent
  - Avoids obstacles
- `provideHint()`: Uses BFS to suggest next cell in shortest path to end
- `resetPath()`: Clears all selections, resets stats

#### Levels & Stats

- Buttons load predefined maps of increasing complexity
- Grid rebuilds on level change
- Score formula: `100 - moves*2 - hintsUsed*10`
- Achievements unlocked by performance and milestones

#### UX Enhancements

- Keyboard shortcuts: R (reset), H (hint), C (check)
- Local storage saves high scores
- Error messages on invalid actions

---

## Algorithms Used

- **Path Validation**: Linear scan through path array; verifies rules using adjacency and type checks.
- **Hint System (BFS)**: Breadth-first search from current cell to end, finds shortest valid path, highlights next step.
- **Adjacency Check**: Ensures moves are up/down/left/right only (no diagonals).

---

## Creative Features

- Patriotic “stars and stripes” visual theme
- Dynamic difficulty scaling via multiple level maps
- Achievement badges for challenge goals
- BFS-powered hint system to mimic AI pathfinding
- Real-time feedback and stat tracking for replayability

---

American Path Quest transforms a graph traversal problem into an engaging game experience with visual flair, educational value, and strategic path planning.