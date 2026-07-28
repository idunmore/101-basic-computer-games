# hello.bas

This program required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

Lines longer than 72 characters (MS-BASIC's line-length-limit) were split onto additional lines.

Abbreviated keywords (`GOT`, `GOS`, `INP` and `PRI`) were expanded to the unabbreviated keyword, since MS-BASIC doesn't support these abbreviations.

The routine at line 500 was an unnecessary loop to print the player's name, character by character.  Simply `PRINT`ing the entered string works fine here.
