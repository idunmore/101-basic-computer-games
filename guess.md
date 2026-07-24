# guess.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Most of the line numbers after line 25 (and some before) were either incorrectly OCRd/transcribed, OR, what looks more likely, is that AI tried to "fix up" the OCR output to "make sense".

I corrected these per the original listing.

## Porting

Porting involved:

1. Replacing `RND(0)` calls with our target MS-BASIC versions intentional equivalent `RND(1)`.

2. Expanding keyword abbreviations such as `PRI` to `PRINT` and `GOT` to `GOTO`.
