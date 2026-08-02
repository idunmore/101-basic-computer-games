# hockey.bas

This program required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

Changed `RND(X)` calls to `RND(1)` so they generate new values on each call.

*Strictly speaking, the code will run unchanged, but since `X` begins at zero, the random value is invariant for that sessions*.
