# craps.bas

This program required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

Porting this required:

It began with usual removal of `RANDOMIZE`  and switching `RND(0)` calls to `RND(1)` .

The "Are you ready?" evaluation (line 216) is written in a way that infers that a `false` condition executes the statement after the  statement separator.  For MS-BASIC "else if" needed to be move on a subsequent line (line 217), which required renumbering lines between 216 and 219.
