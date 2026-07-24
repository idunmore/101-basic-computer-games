# slots.bas

This program required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

Porting involved:

1. Removing the unsupported `RANDOMIZE` on line 100.

2. Replacing `RND(0)` calls with our target MS-BASIC versions intentional equivalent `RND(1)`.

3. Replacing `\` statement separators with `:`

4. Changing the `INPUT $A`, and surrounding logic, to use `A$` instead, at line 560.

5. I made some minor print-formatting changes to work around `TAB()` not functioning the same way as the source BASIC dialect, so that the reel symbols would print intelligibly.
