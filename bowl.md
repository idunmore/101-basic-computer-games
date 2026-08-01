# bowl.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Fixed transcription issues that resulted in syntax errors for `PRINT` and array references.

## Porting

The usual adjustments for random numbers (`RND(I)` to `RND(1)` etc.).

Syntax changes for statement separators from `\` to `:` and `REMARK` to `REM` (strictly speaking, MS-BASIC interprets this as `REM` `MARK`, so does not *have* to be changed).

Two unsupported functions/modifiers are used in the original listing:

- Using `MAT` to initialize arrays to `0`.
- Handling `TAB()` modifiers.
