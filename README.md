# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/panji81/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/panji81/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

An original chess engine in a single 4 KB Python file: 0x88 board, negamax alpha-beta search with principal-variation search, null-move pruning, late-move reductions, quiescence over captures and check evasions, transposition table, killer + history move ordering, and iterative deepening on a fixed 120,000-node budget — deterministic, no model calls, no clock. It plays a full trial through the make.fun environment (the grader sets `MAKEFUN_ENV_URL`, `MAKEFUN_TRIAL_SEED` and `MAKEFUN_PROMPT_FILE`).

## Run it

```sh
python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
