# bingo.bas

This program required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

A number of changes were necessary to make `bingo` run:

The `RANDOMIZE` call was removed as it is neither supported nor necessary.  Also, the calls to `RND` were replaced with `RND(1)` as that is the MS-BASIC equivalent.

"Our" version of MS-BASIC did not implement the `MAT` instructions, so the original code below doesn't work (it should read the letters in the `DATA` statement into the `A$` array):

````
210 MAT READ A$(5)
220 DATA B ,I ,N ,G ,O
````

That's a quick and easy fix:

````
140 FOR I=1 TO 5: READ C$: A$(I)=C$: NEXT I
150 DATA B ,I ,N ,G ,O
````

You may notice the change in the line numbers.  This was necessary as when the original code jumps back to line 180 to start a new game, the various DIM statements are re-run and that throws a `reDIMensioning` error.

So the array initialization (`DIM`s) are moved up before the "restart" line of 180.

Line 185 is required as the `V` and `W` variables are used to indicated which player won, but there is a case where the code evaluates them before they are set.  This works fine on the **first** run, because they default to `0`, but if you choose to play again, immediately after the first number is called, they `V` and `W` will still be set from the prior game and whichever player won *that* will instantly win the next game, also.

So ... we just just reset them both to `0` on restart.

Finally, lines 190-230 clear out the `B` array of prior values to ensure it is in the same state as the first game, otherwise the game fails on replay while checking for BINGOs, as only the **new** card information is re-written to `B` on replay and not the old numbers in the arrays that are checked against it.
