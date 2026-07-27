# even1.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Some line numbers and calculations and comparisons were incorrectly OCRd/transcribed from the printed listing.

## Porting

`RANDOMIZE` statement was removed, and an `RND` reference was replaced with a syntactically, and functionally, correct `RND(1)` .

Line 3 (in the original printed listing) references a non-existent line number as an (implied) `GOTO` target.  Either the original target version of BASIC would simply pick up the NEXT line it could find that was higher than the target line number, or this program could **not** have run *as printed*.
