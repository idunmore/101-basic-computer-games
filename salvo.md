# salvo.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

I did a couple of obvious changes, and then ran into issue after issue, so I turned this one over to Codex (this is the fourth program out of 94 I used any AI assistance on).

*It took multiple iterations with the AI to first get it running and then to find, and fix, some infinite loops in the converted version.*

I let Codex document the changes as well, since they were too numerous to track manually.

## OCR/Transcription Corrections

-   Incorrect ship-placement formulas at 1280 and 1300–1380:
    -   Wrong sign in  `FNB`
    -   Missing  `X`,  `Y`, and direction multiplications
    -   Coordinates stored in the wrong arrays
    -   Incorrect loop limits
-   Reversed proximity test at 1430.
-   Incorrect ship definitions:
    -   Battleship stored as code  `5`  instead of  `3`
    -   Cruiser requested four coordinates instead of three
-   Wrong hidden command at 1730.
-   Shot-count calculations tested for empty squares rather than surviving ships.
-   Missing successful exit from coordinate validation at 2360.
-   Reversed “already fired here” test at 2390.
-   Incorrect previous-turn expression at 2440.
-   Computer board scans used the wrong array and sometimes ran to row 12 rather than 10.
-   Lines 2910–2940 assigned random coordinates and directions to the wrong variables.
-   Numerous corrupted variables in the computer targeting section, such as  `H3`  for  `R3`,  `H2`  for  `R2`, and  `W9`  for  `Q9`.
-   A hit was recorded in array  `A`  instead of the player’s board,  `B`.
-   The sunk-ship calculations compared the wrong values and contained malformed parentheses.
-   Much of the probability-grid logic at 3810–4200 used the wrong arrays, variables, comparisons, and constants.

## Porting

-   Split all source lines longer than 72 characters without shortening their text.
-   Used  `:`  for the few same-line statement separators.
-   Changed random-number calls to  `RND(1)`.
-   Left  `RANDOM`  only as part of a  `REM`  comment.
-   Retained the supported  `DEF FNA`  and  `DEF FNB`  functions.
-   Added line 1405 to bypass the nonexistent previous-ship comparison for the first ship. This avoids entering  `FOR Z3=1 TO 0`, which this MS-BASIC does not treat as an empty loop.
-   Replaced the nested  `FOR`  loops at 1410–1450 with explicit counters. This prevents line 1435 from repeatedly jumping out of active loops and disturbing MS-BASIC’s loop-control stack.

## Gameplay

This game plays quite slowly, so be prepared.

The initial board setup by the computer will look like nothing is working, but give it a minute.

Once the game-proper is underway, it can take *minutes* (running a 1MHz clock) for the computer to process your shots, apply the results, and generate its own shots in return.
