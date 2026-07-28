# furs.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Only two issues:

- An incorrectly converted line number (line 508 was read as 506, which caused and error when line 508 was a `GOTO` target).

- Lines 1176 and 1177 converted the final `/10^2` divisors as `/0^2` causing an instant divide-by-zero error.

## Porting

`RANDOM` statement was removed, and an `RND(0)` references were replaced with syntactically, and functionally, correct `RND(1)` .
