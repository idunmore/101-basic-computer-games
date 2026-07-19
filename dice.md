# dice.bas

This program required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

- Multi-statement lines were changed to use `:` as the statement separator instead of `\`.
- Calls to `RND` were changed to `RND(1)`, per MS-BASIC syntax/behavior.
