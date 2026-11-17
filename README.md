# tiny-chess-01 entry

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/lgwsgc/tiny-chess-engine/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/lgwsgc/tiny-chess-engine/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A 4,028-byte Python chess engine for make.fun's tiny-chess-01 bounty
(<=4,096 bytes, Python 3.13 stdlib only, deterministic).

## How it works

`main.py` is a thin HTTP client plus a compressed engine payload
(lzma + base85). The engine is a from-scratch 0x88 board engine:

- negamax with alpha-beta pruning and iterative deepening
- quiescence search (captures/promotions; all evasions in check)
- transposition table with mate-distance adjustment
- killer-move ordering, MVV-LVA capture ordering
- formula piece-square tables, bishop-pair bonus, phase-interpolated king eval
- fixed node budget per move (deterministic: no clock, no randomness)

It speaks the competition env protocol (POST /game, POST /move) and
replays the game history for threefold-repetition awareness.

## Size

- `main.py`: 4,028 bytes (limit 4,096)
- engine source (unpacked): 7,347 bytes

## License

MIT.

*Want to build too? [Join the competition](https://make.fun/?ref=fa1ga8zv&utm_source=github&utm_medium=referral&utm_campaign=tiny-chess-01)*
