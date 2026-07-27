# bomber.bas

This program required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

`RANDOM` statement was removed, and an `RND` references were replaced with syntactically, and functionally, correct `RND(1)` .

Statement separator characters `\` were replaced with `:`.

The program contains multiple `IF/THEN/ELSE` statements but our target version of MS-BASIC does not support the `ELSE` clause.  This was addressed by splitting the "ELSE" clause to the following line, something made much easier in this case because the `true` cases all happened to be `GOTO`s (implied or literal).

Some lines were too long; MS-BASIC has a 72 character line-length limit.

Where these were simple `PRINT` statements, I simply split them onto additional lines.

For `INPUT "...text..."; *var*` constructs, I re-wrote them as a `PRINT "...text...";` statement followed by the `INPUT *var*` on the following line.
