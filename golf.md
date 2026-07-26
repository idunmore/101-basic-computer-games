# golf.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Changes here were mostly minor OCR issues such as variable name, type or value transpositions, with a couple of   `GOTO`  target line numbers getting altered.

## Porting

Porting was interesting:

That began with usual removal of `RANDOMIZE`  and switching `RND(X)` calls to `RND(1)` (`RND(X)` would also work as `X` *appears* to always be >0, but it doesn't do anything different, so `RND(1)` was used to save on the number of tests needed).

The lines that print the instructions, between 230 and 270 were too long (>72 characters) for MS-BASIC, so were shortened by using a string variable in place of a literal string.
