# mathd.bas

This program required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

- Removed the unsupported `RANDOMIZE` command, but left a `REM` as the line (100) was the target of several `GOTO` statements (making the change smaller).
- Calls to `RND(0)` were replaced with `RND(1)`, per MS-BASIC syntax/behavior.
