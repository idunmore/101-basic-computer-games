# reverse.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Various name and value transcription errors; line 410 was using `I` as the loop variable instead of `K`, etc.


- Corrected the depth calculation for cratering, changing `W*2777` to `W*.277`

## Porting

- Replaced `\` statement separators with `:`

- Changed `RND` calls with `RND(1)`

- Prevented trying to reverse less than 2 items, and fixed issues with the reverse routine going negative.
