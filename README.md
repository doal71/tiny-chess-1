# tiny-chess-1

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/doal71/tiny-chess-1/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/doal71/tiny-chess-1/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A 4 KB chess engine in Python: 0x88 board, legal move generation
(castling, en passant, promotion), negamax alpha-beta with a
transposition table, killer moves, late-move reductions, null-move
pruning, and quiescence (captures, promotions, and all evasions when
in check). Evaluation is PeSTO tapered: Texel-tuned middlegame/endgame
piece-square tables with separate endgame material values. The
search is repetition-aware: a game-history table records every
position played, and a repeated position scores 0, so the engine
refuses draws in won positions instead of shuffling into
threefold repetition. Promotion codes are mapped to the right
pieces (queen, rook, bishop, knight), fixing a bug where a queen
promotion placed a knight and the engine never promoted to queen.

Search is a fixed node budget (75,000 nodes per move, iterative
deepening at the root), so it is deterministic and never uses a clock.
About 21,400 nodes/second; a move takes at most ~3.5 s, well under
the 10 s limit.

- `main.py` is the whole engine: 3,444 bytes, packed by the kit's
  `makefun compress` from the readable `source.py`. Python 3.13,
  standard library only. It reads, imports or execs no other file
  in the repository.
- `source.py` is the readable source (7,595 bytes). It is not part of
  the submitted repository; `makefun bundle` sends it beside the
  sessions.

## Practice results (local, kit's practice trials)

| trial | W-D-L | Elo |
|-------|-------|-----|
| trial-0 | 3-2-1 | 1,451 |
| trial-1 | 4-1-1 | 1,545 |
| trial-2 | 5-0-1 | 1,654 |

Mean practice Elo about 1,550, above the 1,154 needed to enter the
final. Move generation is verified by perft (startpos, Kiwipete,
and four other standard positions, depths 1-3, all exact).

## Run it

```sh
python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=1808df0a&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
