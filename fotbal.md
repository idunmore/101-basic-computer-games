# fotbal.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

There were a lot of these, and I stopped writing them down as I was making them.  I did not feel like manually going back and filling in the ones I hadn't noted from a file diff.

So, as an experiment, I let Codex (AI) take a stab at describing and summarizing the OCR/transcription fixes/changes:

-   Line 4 was missing the colon after  `DATE`.
-   Line 160 incorrectly sent  `"YES"`  back to the question:
    -   Incorrect:  `IF A$="YES" THEN 150`
    -   Correct:  `IF A$<>"YES" THEN 150`
-   Instruction lines 223–230 had been omitted or assigned the wrong line numbers.
-   Line 520 had a malformed array reference:  `C(10+L;`.
-   Line 600, the  `HALF-BACK OPTION`  chart entry, was missing.
-   Several long decorative lines were truncated:
    -   Tear-off line
    -   70-character field divider
    -   Plus-sign divider
    -   Field ruler
-   Kickoff messages around lines 770–830 had missing blank lines, altered spacing, and changed punctuation.
-   Line 895 contained two errors:
    -   `P+Y(T)+10`  →  `P+Y(T)*10`
    -   `=X(T)`  →  `>=X(T)`
-   Line 936 ended with a period instead of a comma.
-   Line 940 was missing its trailing semicolon.
-   Line 1000 incorrectly referenced nonexistent  `R()`  entries instead of comparing  `A(P1)`  with  `B(P2)`.
-   Line 1110 branched to nonexistent line 1330 instead of touchdown line 1320.
-   Line 1190 appeared twice.
-   Line 1440, which calculates runback distance  `R`, was entirely missing.
-   Lines 1490 and 1500 used equality tests where the original used  `>=`.
-   Line 1780 contained  `3`  instead of  `9`, making Team 2’s play table invalid.

## Porting

I *did* keep track of the material code changes myself, so:

Very little was required here, just `REM`oving the `RANDOMIZE` call (line 920), but leaving the line present as it is a `GOTO` target.

Replacing random number generation calls with `RND(1)`.

The "still haven't figured out what MS-BASIC's `TAB()` modifier is meant to do" calls were replaced with various space calculation/printing loops (play chart, down and distance and field position arrow).

Some lines exceeded the 72-character line-length limit so had to be split.

Added semicolons to `PRINT` statements where needed.
