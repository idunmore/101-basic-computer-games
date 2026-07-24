# blkjac.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Line 115 has a period after the line number, which is syntactically invalid; the period just needs to be removed.

## Porting

Porting involved replacing `RND(0)` calls with our target MS-BASIC versions intentional equivalent `RND(1)`.
