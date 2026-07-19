
# aceydu.bas

This programs required adjustments to the code as part of porting it.


## OCR/Transcription Corrections

**None.**

## Porting

The unsupported command `RANDOMIZE` was removed (line 100), and the three lines (270, 300 and 730) that used `RND` were changed to `RND(1)`.
