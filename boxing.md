# boxing.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Some common errors, including transposition of `B` for `8` and `I` for `1`, which caused both calculation and `FOR/NEXT` errors ("next without for" in the main "rounds" loop).

Some `PRINT` separation characters were missing/incorrect.

Line 980 was read as 981, and looking at the listing it is easy to see why, but this was a `GOTO` target (a knockout), so that results in a runtime error.

## Porting

Changed `RND` references to `RND(1)` as required by MS-BASIC.
