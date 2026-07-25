# buleye.bas

This program required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

Porting involved:

1. Replacing a `RND` call with our target MS-BASIC versions intentional equivalent `RND(1)`.

2. Switching `\` statement separators to `:`.

3. Changing an assignment in line 100 from `R,M=0` to `R=M=0`.

4. Removed a `,` in line 80, to properly align the scores.

5. Moving the `FOR` statements at the end of line 100 onto its own line 105 (an alternative would have been to add a statement separator before it).

6. Removing the superfluous `FOR` statement at the end of line 350.
  This may have been a remnant from printing ALL the scores at the end of the game, though it would need to be on the line above for that to work, but since there is not closing `NEXT` I assumed it was left in the code in error (wouldn't cause one, but doesn't anything, either).
  