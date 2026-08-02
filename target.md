# target.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

`R1` is assigned an illegal value, so corrected that from `57,296` to `57.296`

Fixed the `GOTO 8220` so it targets the correct line `820`.

Fixed the range-rounding expressions (restored the multiplication).

## Porting

Replaced the original `\` statement separators with the correct MS-BASIC one `:`.

The now-so-common removal of `RANDOMIZE` and switch of `RND` references to `RND(1)` calls.

MS-BASIC doesn't have a built-in constant/keyword for `PI`,  so replaced that with a reference to `P` which is initialized to `3.141592` on the first line of the program.

Split/modified lines longer than 72 characters onto multiple lines so they fit within MS-BASIC's line-length limit.

Added `;` `PRINT` separators where required.
