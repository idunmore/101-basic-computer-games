# calndr.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

I only encountered one OCR/transcription error.  Line 180 had been interpreted as:

````
180 FOR I=1 TO 12
````

The actual line is:

````
180 FOR N=1 TO 12
````

## Porting

This was ported, with *caveats*:

The program runs, and produces the correct values in its output (bear in mind it is setup to print the calendar for **1973**!).

The formatting of the day numbers is not, however, correct.

This is due to a mismatch in how the `TAB()` modifier in `PRINT` statements works compared to a) the dialect of BASIC the original was written for and b) compared to other BASIC dialects for which it is documented.

Addressing this is likely to require making changes to MS-BASIC itself; something I may tackle once I've finished the initial porting of the full 101 programs.

What **was** changed:

`REM` statements replaced the original listings use of `'` for comments.

The implicitly dimensioned array `M` exceeded MS-BASICs limit of 10 elements, so an explicit `DIM` for the required 13 elements was added on line 155.

Statement separators were changed from `\` to `:`.
