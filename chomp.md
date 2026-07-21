# chomp.bas

This program required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

Only two changes were made:

- Moving the dimensioning of the array `A` from line 350 to line 107.
  
  This line *could* originally get executed **after** the array has already been referenced (and implicitly created) on line 560, which results in a "redimensioning" error in the target version of MS-BASIC.

  Moving it to line 107 ensures it is dimensioned before it is ever accessed.

- Since the terminals TAB width may not be defined, and attempts to do so have no effect, I modified line 620 to add spaces to the `PRINT` command to the column numbers line up properly with the column contents.
