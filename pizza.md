# pizza.bas

This program required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

Porting this required:

1. Removal of `RANDOMIZE`  and switching `RND` calls to `RND(1)` .

2. The `DATA` statement on line 200 exceeded MS-BASIC's line-length limit and had to be split into two lines.

3. The `PRINT` statement on line 340 exceeded MS-BASICs's line-length limit and had to be split into two lines.
