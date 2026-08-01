# battle.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Mostly errors in comparisons, transposing `=` for `>` or `<` for `=`, and variations there of.

Some assignment errors, also.

## Porting

The usual adjustments for random numbers (`RND(0)` to `RND(1)` etc.).

Changing subscript syntax from `[]` to `()`.

Replacing/re-implementing constructs such as `MAT`, `GOTO OF` (for `ON x GOTO`), and `MIN`/`MAX` with discrete alternatives.

Some boundary/placement issues also resolved.
