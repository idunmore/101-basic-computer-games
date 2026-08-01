# yahtze.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Fixes numerous corruptions/transcription errors that lead to a variety of issues, including broken re-roll loops, scoring, bonus handling, summaries and winner selection.

## Porting

- `TAB()` modifier was replaced with fixed spacing output.

- `CHANGE` and `MAT` keywords were replaced with inline/alternate implementations of the same functionality as they are not supported.

- `RANDOMIZE` removed as it is not necessary nor supported.

- All `RND(-1)` (and similar) instances replaced with `RND(1)` to get the desired random behavior.
