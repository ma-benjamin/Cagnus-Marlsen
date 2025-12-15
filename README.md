## Introduction
A Python-based chess engine that plays standard chess with the added rule of forced captures. This engine is based on and extends from the Sunfish chess engine, with changes in the gen_move function to enfore the forced capture rule, and suppor the Xboard protocol. 

# Running the Engine
To run with Xboard:
`xboard -fcp polyglot-chess -fd Cagnus-Marlsen`

# Features

1. Built around the simple, but efficient MTD-bi search algorithm, also known as [C*](https://www.chessprogramming.org/NegaC*).
2. Filled with classic "chess engine tricks" for simpler and faster code.
3. Efficiently updatedable evaluation function through [Piece Square Tables](https://www.chessprogramming.org/Piece-Square_Tables).
4. Uses standard Python collections and data structures for clarity and efficiency.

