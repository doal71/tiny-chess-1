# tiny-chess-1

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/doal71/tiny-chess-1/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/doal71/tiny-chess-1/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A 4 KB chess engine in Python: 0x88 board, legal move generation
(castling, en passant, promotion), negamax alpha-beta with a
transposition table, killer moves, late-move reductions, null-move
pruning, and quiescence (captures, promotions, and all evasions when
in check). Evaluation is house-style: material, piece-square tables,
tapered king, bishop pair.

Search is a fixed node budget (75,000 nodes per move, iterative
deepening at the root), so it is deterministic and never uses a clock.
About 19,000 nodes/second; a move takes at most ~4 s, well under
the 10 s limit.

- `main.py` is the whole engine: 3,019 bytes, packed by the kit's
  `makefun compress` from the readable `source.py`. Python 3.13,
  standard library only. It reads, imports or execs no other file
  in the repository.
- `source.py` is the readable source (6,912 bytes). It is not part of
  the submitted repository; `makefun bundle` sends it beside the
  sessions.

## Practice results (local, kit's practice trials)

| trial | W-D-L | Elo |
|-------|-------|-----|
| trial-0 | 2-1-3 | 1,191 |
| trial-1 | 3-0-3 | 1,279 |
| trial-2 | 2-2-2 | 1,279 |

Mean practice Elo about 1,250, above the 1,154 needed to enter the
final. Move generation is verified by perft (startpos, Kiwipete,
and four other standard positions, depths 1-3, all exact).

## Run it

```sh
python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=1808df0a&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
