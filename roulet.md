# roulet.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

-   Line 1030 contained an unterminated  `PRINT "`  statement.
-   The welcome message, good-luck message, and blank lines were shifted from their original line numbers.
-   The result for “RED, EVEN, COLUMN 1” was numbered 2980 instead of 3290, leaving branches to 3290 unresolved.
-   Line 4460 appeared twice.
-   Several required  `PRINT`  commas and semicolons were missing, altering indentation or causing unintended line breaks.
-   Several numeric values were placed directly beside strings without separators.
-   `Y OU LOST`  was corrected to  `YOU LOST`.  This is not a transcription error; the issue exists in the original printed listing.

## Porting

-   Replaced implicit  `PRINT`  concatenation with explicit semicolons.
-   Split long output statements while preserving their displayed text.
-   Replaced the slow 0-to-10000 loops used to validate bets with direct range and  `INT()`  checks.
-   Enforced the advertised minimum bet of $1.
-   Replaced the loop used to validate a selected number with direct checks for an integer from 0 through 36.
-   Used the supported  `RND(1)`  form for generating the wheel result.
-   Corrected an original logic error in which 26 and 27 had their colors reversed:
    -   26 is black.
    -   27 is red.
-   Updated the table, result-dispatch lists, and red/black payout test consistently.
-   Added explicit  `GOTO`  syntax where needed.
