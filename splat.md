# splat.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

-   Line 95:  `ISPLAT!`  was a damaged rendering of  `'SPLAT'`.

-   Line 125: the terminal-velocity variation expression had lost its  `+`  and  `-`  operators. It should calculate:  

    `V=V1+V1*RND(0)/20-V1*RND(0)/20`

-   Line 131:  `V#V1`  should have been  `V=V1`, with the same missing  `+`  and  `-`  operators as line 125.

-   Line 145: the acceleration formula had a multiplication sign where a plus sign belonged:  

    `A=A2+A2*RND(0)/20-A2*RND(0)/20`

-   Line 405:  `FOR I=1 TO T`  should have been  `FOR I=I TO T`; the calculation must continue from the time terminal velocity was reached.

-   Line 510:  `K#0`  should have been  `K=0`.

-   Lines 650–690:  `K=K1`  was a misreading of  `K-K1`. These comparisons rank the jump using the number of earlier jumpers who opened lower.

-   Line 1010: the period before  `"SPLAT"`  was a corrupted output separator; it should have been a comma.

## Porting

- `REM`moved  `RANDOMIZE` and `RND(0)` replaced with `RND(1)`.

- File-based disk-leaderboard can't be implemented, so a 100-jump memory-based table was added instead.

- Loops modified to prevent premature exit while active (which messes up the stack).

- Added validations for zero velocity, acceleration and time.
