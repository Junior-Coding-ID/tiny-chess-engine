# Tiny Chess

A strong chess engine in 4 KB of Python (make.fun tiny-chess-01).

`main.py` is the entrypoint: a packed engine (LZMA payload, written by the
kit's `makefun compress` from `engine.py`, the readable source it was packed
from). It plays by the make.fun engine protocol over HTTP (`MAKEFUN_ENV_URL`).

- 0x88 board, alpha-beta with iterative deepening to a fixed 150,000-node
  budget per move, quiescence over captures, promotions and replies to check
- Transposition table, killer moves, MVV-LVA capture ordering, Zobrist keys
- Material + piece-square evaluation, bishop pair, deterministic (no clock,
  no unseeded randomness), standard library only

Practice trial-0 (local, kit scorer): Elo 1279 at 200,000 nodes; this
150,000-node build trades a little strength for a safe margin under the
10 s/move limit.
