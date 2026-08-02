# hi-q.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

The original `DIM B(70)` was OCRd/transcribed as `DIM B(7,8)`, so I corrected this.

Lines 31 and 32 were misread/translated, and needed correction (e.g. doing equality comparisons instead of the original's subtraction).

Some operators were converted as `=<>` and were corrected to `<>`.

The replay `GOTO` target line number was incorrect.

## Porting

Replaced the original `\` statement separators with the correct MS-BASIC one `:`.

Swapped the `TAB()` implementation for a fixed-spaced implementation.
