# Sudoku Solver — CSP with AC-3 & Backtracking

A Sudoku solver using **Constraint Satisfaction Problem (CSP)** techniques. It combines **AC-3 arc consistency**, **MRV heuristic**, and **backtracking with forward checking** to efficiently solve puzzles from Easy to Very Hard.

---

## Features

- Solves any valid 9×9 Sudoku puzzle
- Supports multiple difficulty levels: Easy, Medium, Hard, Very Hard
- Uses **AC-3** to eliminate impossible values before searching
- **MRV (Minimum Remaining Values)** heuristic picks the most constrained cell first
- **Forward Checking** prunes domains after every assignment
- Tracks **backtrack calls and failures** for performance analysis

---

## How It Works

### 1. CSP Formulation
- **Variables:** Every cell `(row, col)` in the 9×9 grid
- **Domains:** Pre-filled cells have a single value; empty cells start with `{1-9}`
- **Constraints:** No two cells in the same row, column, or 3×3 box share a value

### 2. AC-3 (Arc Consistency)
Runs before search begins to eliminate values that violate constraints, drastically reducing the search space.

### 3. MRV Heuristic
Always picks the unassigned cell with the **fewest remaining legal values** — fails faster on bad paths.

### 4. Backtracking + Forward Checking
After assigning a value, **forward checking** propagates constraints to neighbors via AC-3. If any domain becomes empty, it backtracks immediately.

---

## How to Run

### Requirements
- Python 3.x
- No external libraries needed

### Setup
Place your puzzle files in the same directory as the script. Each file should be a 9-line text file where `0` represents an empty cell:

```
530070000
600195000
098000060
800060003
400803001
700020006
060000280
000419005
000080079
```

### Run
```bash
python sudoku.py
```

The solver will automatically attempt: `easy.txt`, `medium.txt`, `hard.txt`, `veryhard.txt`

---

## Output Example

```
--- Solving easy.txt ---
534678912
672195348
198342567
859761423
426853791
713924856
961537284
287419635
345286179
Calls: 1 | Failures: 0
```

---

## Project Structure

```
├── sudoku.py        # Main solver
├── easy.txt         # Easy puzzle
├── medium.txt       # Medium puzzle
├── hard.txt         # Hard puzzle
├── veryhard.txt     # Very Hard puzzle
└── README.md        # This file
```

---

## Concepts Used

| Technique | Purpose |
|-----------|---------|
| AC-3 | Arc consistency / constraint propagation |
| MRV Heuristic | Smart variable selection |
| Forward Checking | Early failure detection |
| Backtracking | Systematic search with undo |
