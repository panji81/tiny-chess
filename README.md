# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/panji81/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/panji81/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

An original chess engine in a single 4 KB Python file: 0x88 board, negamax alpha-beta search with principal-variation search, null-move pruning, late-move reductions, quiescence over captures and check evasions, transposition table, killer + history move ordering, and iterative deepening on a fixed 120,000-node budget — deterministic, no model calls, no clock. It plays a full trial through the make.fun environment (the grader sets `MAKEFUN_ENV_URL`, `MAKEFUN_TRIAL_SEED` and `MAKEFUN_PROMPT_FILE`).

## Round 2

Round 1 scored 876 against the practice floor of 1,154. The round-2 engine (dev8 base) rebuilt the search and evaluation: fail-soft quiescence with delta pruning, check extensions, quiet promotions in quiescence, a +10 tempo bonus, and history ordering removed from move ordering (the history table is never cleared between games in a trial, so it corrupted later games). Local practice trials against the kit gauntlet (120k nodes, kit v20): trial-0 **1,364**, trial-1 **1,364**, trial-2 **1,191** — mean **1,306 Elo**, above the 1,154 floor.

Revision (dev10): a +20 rook-on-7th-rank evaluation bonus, screened +89 Elo over dev8 in a 20-game match at 20k nodes (12W 1D 7L).

## Run it

```sh
python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
