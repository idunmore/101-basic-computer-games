# change.bas

This program required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

Code changes were limited to:

- Changing statement separators from `\` to `:` for multi-statement lines.

- Splitting statements following implied and `GOTO` in `IF/THEN` multi-statement lines so the non-matched, *implied `ELSE`), condition actually runs.

  The following code appears to simulate `IF/THEN/ELSE` in the **original dialect** of BASIC the code was written for:
  ````
    10 IF A = 1 THEN GOTO 30: PRINT "ELSE"
    20 END
    30 PRINT "THEN"
   ````

However, in MS-BASIC, the `PRINT "ELSE"` will never execute, and it has to be moved to the following line.
