# poet.bas

This program required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

A number of changes were necessary to make `bingo` run:

The `RANDOMIZE` call was removed as it is neither supported nor necessary.  Also, the calls to `RND` were replaced with `RND(1)` as that is the MS-BASIC equivalent.

The **big** change here was re-writing the code to work without having support for an `ELSE` clause for `IF/THEN` statements.

There's nothing particularly complicated about that ... here you would just need to put the code that would run in the `ELSE` case on the next line, since the `IF` clause was just jumping to the next line of code.

However, in a line-numbered BASIC that requires having "spare" line numbers between the main lines of code ... and in **poet.bas** the line numbers had no "gaps" ... it's 100, 101, 102, etc.

This necessitates completely renumbering most of the file, including all the `GOTO` targets.  The target version of MS-BASIC does not have a "renumber" command, so this was done manually (faster than writing a script to do it, since the program is small, but probably not by much).
 