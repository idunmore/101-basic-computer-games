# cube.bas

This program required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

Strictly speaking the game will run as-is, however the `RND(X)` calls always produce the same number, for that program run, in MS-BASIC (since `X` is always `0`), so it makes for a rather pointless "game".

So, the only change was to replace `RND(X)` with `RND(1)` which yields the correct (and intended) random number generation behavior.
