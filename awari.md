# awari.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

A surprisingly large number of error-causing/logic-breaking OCR/transcription errors were found, relative to most of the other programs (this may be due to the density of the listing).

These included incorrect variable names/assignments, missing spaces, math operator transposition (`+` for `*` etc.), missing operators, comparison operators being transposed and incorrect variable value assignment and incorrect line numbers for `GOTO` statements.

## Porting

As noted in the "[LEARNINGS.md](https://github.com/idunmore/101-basic-computer-games/blob/main/LEARNINGS.md)" file, MS-BASIC **always** executes the code in a `FOR/NEXT` loop **at least once**, even if the exit condition is already met.  This causes the original code to immediately fail as it tries to read `DATA` that isn't present.

To avoid that, I put guard clauses ahead of zero-iteration loops.

I also added spaces between keywords and expressions to make things more readable while adjusting the code.
