# mugwump.bas

This file required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Lines 330 and 340 were corrected to read as `<>` (not equal) comparisons, rather than just `<`.  Without this, if your guesses for each direction were *lower* than the position of a **mugwump**, it would be counted as "found".

Entering 0, 0 as your guess would instantly find ALL mugwumps as as result.

## Porting
Line 5, "`RANDOMIZE`" was removed, as this command is not supported in the target version of MS-BASIC (and is not necessary anyway).

On line 1020, I changed the argument for `RND()` from 0 to 1.  Using zero always generates the same result, where as 1 yields the desired behavior (a floating point number between 0 and 9.999999999).