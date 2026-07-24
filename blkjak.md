# blkjak.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Line 115 has a period after the line number, which is syntactically invalid; the period just needs to be removed.

Numerous instances of variables assignments of `I` or increments by `I` had been transcribed as `1` and had to be corrected.

Several line numbers were misinterpreted; including various that were `GOTO` targets.

Line 201 was missing entirely.

## Porting

Porting involved:

1. Replacing a `RND(0)` call with our target MS-BASIC versions intentional equivalent `RND(1)`.

2. Switching `\` statement separators to `:`.

3. Changing variable assignments that get ASC-II character codes via the `#` operator (i.e., `#A` gets the ASC-II value of the letter "A") to use `ASC("")` instead, such as `L=ASC('A')`).

4. Replacing `INPUT $K` on line 986 with `INPUT K$` and then changing the logic on the following lines to look for `Y` for the replay loop.
