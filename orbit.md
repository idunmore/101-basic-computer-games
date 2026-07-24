# orbit.bas

This program required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

Porting involved:

1. Removing the unsupported `RANDOMIZE` call.

2. Replacing `RND(0)` calls with our target MS-BASIC versions intentional equivalent `RND(1)`.
