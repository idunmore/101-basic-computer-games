# basbal.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Only one error was found, and just a single character at that; the `$` for the `INPUT` statement was read as `S`.

I corrected this per the original listing.

## Porting

Porting involved:

1. Replacing `RND(0)` calls with our target MS-BASIC versions intentional equivalent `RND(1)`.

2. Replacing `\` statement separators with `:`

3. Line 110 sets up three arrays with data from line 300 on.  First value goes into `C`, the next into `X`, the third into `F`.  There ae 19 triples of data like this.  However the `READC` function doesn't exist in our version of MS-BASIC, so I re-wrote this code using constructs that do (lines 110 to 115).

4. Line 140 gets the players team name, one character at a time, to build a character array.  This is unnecessary (and INPUT works differently in the source BASIC dialect), so this was replaced with a simple `INPUT A$` statement.  Then line 250 would have printed the original character array, but that's replaced with `PRINT A$`.

5. I made some minor print-formatting changes, to the underscoring on line 210 and adding some `;` so lines would continue not do a CR/LF, to get back to the original presentation.

6. Commented out the `CHAIN` command on line 580 as it is not supported, but see below:

## On the Program Itself

This is the first part of a two-part program (basbal.bas and basb1.bas), which just prints an interesting introduction and then initiates loading the second part (that's the `CHAIN` command on line 580).

I do not see that anything is set up in this program that is needed by the second one (so to PLAY you can just run that one), so it may just be for "flavor" or it could be that this program is shorter, and it provides something to read/do before the longer loading process for the second part.
