# bug.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Some common errors, including transposition of `B` for `8`, which occurred once in the body output.

## Porting

Changed `RND(0)` references to `RND(1)` as required by MS-BASIC.

Modified the `DIM` statement to use the correct `()` syntax instead of `[]`.

Switched to discrete assignments during initialization instead of chained (`A=B=H= ... 0` etc.), splitting the line at the same time.

Split the `PRINT` statement on line 120 so it fits under MS-BASIC's 72-character line-length limit.

Corrected some reversed tests and completion test and other minor logic shifts between BASIC dialects.

And converted the use of `TAB()` to use fixed spaces to keep the layout correct.
