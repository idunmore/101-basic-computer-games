# fipfop.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Too many to catalog ... so look at the diff in the commit history, but a selection included completely missing lines, lines that do not exist, lines merged into each other, numerous transpositions of variable names (where the listing is very clear and crisp), missed characters (hard to see on those lines in the listing), and so on.

## Porting

Porting involved:

1. Replacing a `RND(Y)` call with our target MS-BASIC versions intentional equivalent `RND(1)` since `Y` would always evaluate as `0`.

2. Removing the unsupported `RANDOMIZE` statement.

3. Moving array dimensioning out of the re-start loop, and adding an array clear-down routine at the top of said loop.
  
 4. Adding/replacing lines that are missing from the original printed listing and, without which, it is hard to see how the game could run (e.g., the routine at line 610 prints the current board state only prints the FIRST character, and the loop, which isn't complete, begins after that ... so only one character is printed).
 