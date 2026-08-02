# hmrabi.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Corrected `INT(/P/2)` to `INT(P/2)`

Changed `B` to `Y` in the harvest report

Fixed the impeachment report so it prints the value of `P` not `'D`.

Corrected the misinterpreted `LET Z=11 THEN 860` so it is the original `IF Z=11 THEN 860`



## Porting

The the usual array of removing `RANDOMIZE`, switching to `RND(1)` calls and swapping the `\`  statement separators to MS-BASIC's `:`.
