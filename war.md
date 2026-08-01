# war.bas

This program required corrections to the OCR/transcriptions.

## OCR/Transcription Corrections

Corrected an error where transcription read an `=` in line 110 that should be `-`; a benign issue since it is just in a `PRINT` statement.

## Porting

Removed the `RANDOM` call and replaced `RND(X)` with the correct (for our purposes) `RND(1)` (because `X` is always zero at this point, and just generates the same number for every call).

Switched the `^G` (CTRL-G ... which "rings" the console "bell") for `CHR$(7)` to it will work correctly on appropriately emulated terminals.

The next fix was in the "shuffle" logic (lines 280-350).  This fell foul of MS-BASIC always executing the loop code **at least once** even if the exit condition was already met; which causes an infinite loop.

My *first* fix for this was to simply avoid entering the inner loop in a case where the "duplicate" is the first and only value in the array.  And this works.

However, the original code "shuffles" the deck by randomly selecting a card from the full 52-card deck every time, and the more cards that have been shuffled the more likely a collision becomes.  This results in **extremely** slow shuffling (minutes on a standard 1MHz "BE6502" build).

I debated leaving that as-is, but ultimately decided to try and optimize the shuffling and, with that done, decided to commit the optimized version but include the original (fixed) lines here.

Try the program with the optimized shuffling first, and then copy/paste the following lines in to get to the original version (they'll just replace the existing code, no manual editing needed):

````
280 FOR J=1 TO 52
290 LET L(J)=INT(52*RND(1)+1)
295 LET D=0:IF J=1 THEN 350
300 FOR K=1 TO J-1
310 IF L(K)=L(J) THEN LET D=1
340 NEXT K
345 IF D=1 THEN 290
350 NEXT J
````

The optimized (in the committed file) uses a "[Fisher-Yates shuffle](https://en.wikipedia.org/wiki/Fisher%E2%80%93Yates_shuffle)", which is many times faster:

````
280 FOR J=1 TO 52
290 L(J)=J
300 NEXT J
310 FOR J=52 TO 2 STEP -1
320 K=INT(RND(1)*J)+1
330 T=L(J):L(J)=L(K):L(K)=T
340 NEXT J
350 REM SHUFFLE COMPLETE
````

 And "no" I didn't just "know" this, I had to do a little research on alternate algorithms.