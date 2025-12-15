## Introduction
A Python-based chess engine that plays standard chess with the added rule of forced captures. This engine is based on and extends from the Sunfish chess engine, with changes in the gen_move function to enfore the forced capture rule, and suppor the Xboard protocol. 

# Features

1. Built around the simple, but efficient MTD-bi search algorithm, also known as [C*](https://www.chessprogramming.org/NegaC*).
2. Filled with classic "chess engine tricks" for simpler and faster code.
3. Efficiently updatedable evaluation function through [Piece Square Tables](https://www.chessprogramming.org/Piece-Square_Tables).
4. Uses standard Python collections and data structures for clarity and efficiency.

Note: Original Sunfish readme is under sunfish_README.md.

# Modifications to Sunfish:
### Forced capture variation
We modified move generation to enforce a “forced capture” rule:
1. Generate pseudo-legal moves.
2. Filter out moves that leave the king in check to get legal moves.
3. Then if any of those legal moves are captures (including en passant), only those capture moves are returned.
4. Otherwise all legal moves are returned.

### Fifty-move rule
We modified the evaluation logic to enforce the fifty-move draw rule:
1. Track the number of half-moves since the last pawn move or capture.
2. Reset this counter to zero whenever a pawn is moved or a capture occurs.
3. Increment the counter after every other move.
4. If the counter reaches 100 half-moves (50 moves per side), the position is treated as a draw and evaluated with a score of 0.

### Threefold repetition
We modified the search to detect threefold repetition and treat it as a draw:
1. Each position is identified using a key consisting of the board state, castling rights, and en passant information.
2. We store how many times each position appears along the current search path in a hash table.
3. When making a move during search, the counter for the resulting position is incremented before searching deeper and decremented afterward.
4. If a position is encountered three or more times during search, it is evaluated as a draw with a score of 0.

# Running the Engine
This chess engine is written in **Python** and runs using **PyPy3**.  
It is connected to XBoard via **Polyglot (chess)**.

### Install PyPy3

```
sudo apt update
sudo apt install pypy3
```

### Assuming PolyGlot (chess) is installed.

### Get absolute path by running:
```
pwd
```

### To run with Xboard (terminal):
```
xboard -fcp polyglot -fd /path/from/pwd
```

### To add engine to Xboard (GUI):
```
Engine Directory: /path/from/pwd
Engine Command: polyglot
```
