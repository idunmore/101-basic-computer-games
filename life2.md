# life2.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

The `TO` in the `FOR/NEXT` statements was consistently interpreted as `T0`, so was changed to the correct `TO`.

Some `:` were interpreted as `;` (or "corrected" to such by AI as they fell after `PRINT` statements.  This lead to syntax errors with multi-statement lines, and those cases were replaced with the correct `:` statement separator.

## Porting

A single case of `TAB(10)` was replaced with spaces (line 500); no fancy logic required for this one.

In the original listing, line 700, the X, Y input request was doing weird things with character literals which, while consistent with the printed listing, just results in unnecessary characters and line-feeds on the input line (which do not show up in the printed sample runs).

So, I just removed them.

Output then matches the printed samples from the book.
