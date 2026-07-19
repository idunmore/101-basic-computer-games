# 1check.bas

This file required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

The original code for printing the numbers for each square on the board uses a formatting string (`B$="## ## ## ## ## ## ## ##"`) in conjunction with the `USING` keyword to print numbers that are always two digits; single digit numbers are left-padded with spaces:

````
70 FOR J=1 TO 57 STEP 8
72 B$="## ##  ##  ##  ##  ##  ##  ##"
74 PRINT USING B$;J,J+1,J+2,J+3,J+4,J+5,J+6,J+7
76 NEXT J
````

The `USING` keyword, and formatting strings, are not supported in the target version of MS-BASIC, so I re-wrote this code as follows:

````
70 PRINT "  1   2   3   4   5   6   7   8"
71 PRINT "  9  10  11  12  13  14  15  16"
72 FOR J=17 TO 57 STEP 8
74 PRINT J""J+1""J+2""J+3""J+4""J+5""J+6""J+7
76 NEXT J
````

The first two rows of numbers are printed as literal strings, to allow for the different width numbers, with the remaining all-2-digit-number rows printed using a variation of the original loop.
