# checkr.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Corrected various `PRINT` separators, also fixed the spelling of "occupying" (this was misspelled in the printed listed, so not an actual OCR issue ... but it was't really a "porting" issue, either).

The third value in the first `DATA` statement was transcribed as `-1` but must be `1` for the game to function, so this was also fixed.

## Porting

The `TAB()` modifier was replaced with fixed-space output, since its behavior is different/questionable in MS-BASIC.

Corrected the comparison for displaying KINGs.

Modified the way nested `FOR/NEXT` was exited with a completion flag so that it exits safely.

And having done the above, the game would run provided you didn't try and show the board.  If you did, it would throw an "out of memory" error.  This was the combined result of nested `FOR/NEXT` loops where the inner loops use the same variable names (some BASIC dialects will treat those inner variables as "local", but not MS-BASIC) as the outer ones, which causes various stack problems and eventually faults, and contained multiple stack frames for `GOSUB`s that were never returned.

Those loops were converted to simple counter-based loops, which also reduces the stack depth, and cases where `RETURN` was used to exit a loop, rather than reaching (directly or via assignment) the terminal condition.
