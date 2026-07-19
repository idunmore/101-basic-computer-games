# kinema.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

The closing parenthesis on line 110 was missing, rendering the line a syntax error.

## Porting

- Line 508, OCR'd/transcribed correctly but appears to be a mistype in the original listing (`PRI` instead of `PRINT`); this was corrected.
- Line 509 misses a space between the `GOTO` and the line number, which was added.
- Calls to `RND(0)` were changed to `RND(1)`, per MS-BASIC syntax/behavior.
