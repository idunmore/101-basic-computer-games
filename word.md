# word.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Changed line 231 from the OCR/transcribed `230 P(J)=L(J)` to `230 P(Q)=L(J)`.

Changed the incorrectly transcribed `232 Q=0+1` to the correct `232 Q=Q+1`.

## Porting

Removed the `RANDOMIZE` call and switch `RND` to `RND(1)`.

A combination of inline code and a subroutine to replace the unsupported `CHANGE` function calls, and all arrays are now numeric. 
