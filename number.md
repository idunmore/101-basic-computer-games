# number.bas

This program required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

-  Calls to  `RND(0)`  were replaced with  `RND(1)`, per MS-BASIC syntax/behavior, and `+1` added to each to get the desired random number in the proper range (1-5 instead of 0-4).
- 
