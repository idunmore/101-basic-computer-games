# gunner.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

A handful of errors, but all serious:

Lines 600 and 610 were transcribed with line numbers 510 and 520 (likely an AI artifact), which as they were a `GOSUB` target causes the game to error out.

Line 450 was OCRd/transcribed as:

````
450 LET B2=2*B/57.3\LET T=46500*SIN(B2)\LET X=T-I\LET E=INT(X)
````

The correct line (with statement separators swapped to the MS-BASIC compatible `:`) does the second calculation and assigns it to `I` not `T`:

````
450 LET B2=2*B/57.3:LET I=46500*SIN(B2):LET X=T-I:LET E=INT(X)
````

That broke the shot distance calculation.

## Porting

Only `REM`oving the `RANDOMIZE` call on line 90, and switching `RND(X)` call to `RND(1)` to get different random numbers, was required.
