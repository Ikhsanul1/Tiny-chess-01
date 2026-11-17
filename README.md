# tiny-chess-01

A chess engine in at most 4,096 bytes of Python, built for the
make.fun tiny-chess-01 competition.

`main.py` is the whole engine: a 0x88 board, negamax alpha-beta
search with quiescence (captures, promotions, check evasions), a
transposition table, killer and history move ordering, and a
piece-square-table evaluation with an endgame king table. It
searches to a fixed node budget, never a clock, so every move is
deterministic. The committed `main.py` packs that source as an
lzma payload with a small unpacker, as the rules allow; the
unpacked source is what the build sessions wrote.

It plays through the env at `MAKEFUN_ENV_URL`: POST /game for the
game in play, POST /move with its UCI move, until the env answers
"done".

License: MIT (see LICENSE).
