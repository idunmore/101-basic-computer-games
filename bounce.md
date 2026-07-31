# bounce.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Line 135 in the original listing was interpreted as 125, which caused the input prompt for time interval to be printed out of order and for the restart `GOTO` to error (missing line number).

## Porting

I'm finding any program using `TAB()` to be fiddly and involved to port, something not helped by a) its different implementation in MS-BASIC vs. other dialects and b) I'm not sure it's working correctly in MS-BASIC in the first place.

*I should probably stop, figure out what the **intended** behavior is for `TAB()` in MS-BASIC, and make sure **that** is correct and if not then fix that (which, if not working as intended, is likely due to serial console output and TAB handling).*

In each case using `TAB()`, the way it has to be addressed is slightly different, here I added subroutines to "space" to a specific column from the current column (lines from 1000-1060), which required adding a "current column tracking" variable (`K`), and then to count digits for positive integers (lines 1100-1160, and interspersing these calls in the main code, changing program flow as necessary to accommodate them.
