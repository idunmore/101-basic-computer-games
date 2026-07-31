# poetry.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Line 1420 was interpreted as `1420 GOTO 1456` instead of the correct line `1450`, which caused an immediate undefined statement error.

The original1610 was omitted entirely; presumably by the following line being read as 1610 instead of 1610 (and thus replacing it), this caused **most** of the remaining lines to get renumbered (presumably by the AI part of the transcription) and thus have the wrong lines targeted by other `GOTO` statements, as those were almost all correct.

Line 1620 was, however, not correct, and was jumping to 1650 instead of 1630.

## Porting

Changed the single `RND(-1)` reference to `RND(1)` to get the desired random number generation behavior.
