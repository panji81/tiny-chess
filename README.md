# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/panji81/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/panji81/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

An original chess engine in a single 4 KB Python file: 0x88 board, negamax alpha-beta search with principal-variation search, null-move pruning, late-move reductions, quiescence over captures and check evasions, transposition table, killer + history move ordering, and iterative deepening on a fixed 120,000-node budget — deterministic, no model calls, no clock. It plays a full trial through the make.fun environment (the grader sets `MAKEFUN_ENV_URL`, `MAKEFUN_TRIAL_SEED` and `MAKEFUN_PROMPT_FILE`).

## Round 2

Round 1 scored 876 against the practice floor of 1,154. The round-2 engine (dev8 base) rebuilt the search and evaluation: fail-soft quiescence with delta pruning, check extensions, quiet promotions in quiescence, a +10 tempo bonus, and history ordering removed from move ordering (the history table is never cleared between games in a trial, so it corrupted later games). Local practice trials against the kit gauntlet (120k nodes, kit v20): trial-0 **1,364**, trial-1 **1,364**, trial-2 **1,191** — mean **1,306 Elo**, above the 1,154 floor.

Revision (dev10): a +20 rook-on-7th-rank evaluation bonus, screened +89 Elo over dev8 in a 20-game match at 20k nodes (12W 1D 7L).

Revision (dev11): the evaluation, move ordering, quiescence, search and root driver were rewritten in a cleaner structure, the dead history table was removed, and a king pawn-shield term was added (+8 per friendly pawn on the three squares in front of the king). Screened +191 Elo over dev10 in a 20-game match at 20k nodes (15W 0D 5L). Local practice trials of the packed entry (120k nodes, kit v20): trial-1 **1,364** (3W 1D 2L), trial-2 **876** (1W 0D 5L) — trial-1 clears the 1,154 floor by 210 Elo; trial-2 came in below it, so the graded trial-0 result decides the submission. Packed main.py is 4,092 bytes (limit 4,096).

Revision (dev12): a behavior-preserving restructure of dev8, written fresh — no new eval terms, no search changes. Verified identical to dev8: 24 positions (move gen, eval, root search at 20k), 6 positions at 120k, and a 20-game match at 20k (10W 0D 10L, Elo +0). Packed-entry trials (kit v20): trial-1 **1,364** (3W 1D 2L), trial-2 **1,191** (2W 1D 3L) — identical to dev8. Packed main.py is 4,059 bytes.

## Run it

```sh
python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
