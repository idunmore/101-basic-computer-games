# queen.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections


-   Line 25 had a stray  `!`  after the closing quotation mark.
-   Line 320 used addition instead of subtraction:

```
320 IF T1+T<>2*P THEN 3200
```

Corrected to:

```
320 IF T1-T<>2*P THEN 3200
```

-   Line 2110 changed the wrong coordinate:

```
2110 LET T=T1-K
```

Corrected to:

```
2110 LET U=U+K
```

-   Two player-win messages were both numbered  `3340`. The first was restored as line  `3330`; otherwise it would be overwritten when entered.
-   Line 3510 identified the winning square as  `150`  rather than  `158`.
-   Line 5060 contained  `/`  between “MACHINE” and “THE”; this was restored as sentence punctuation.
-   The PRINT separator was missing before  `M`  in:

```
210 PRINT "MACHINE MOVES TO SQUARE";M
```

-   Corrected the truncated DATA values:
    
    -   The final  `3`  on line 1520 became  `38`.
    -   The final  `5`  on line 1521 became  `56`.


## Porting

-   Removed  `RANDOMIZE`.
-   Preemptively added a `RESTORE` (on the line where `RANDOMIZE` was so the line number was still available/valid) based on odd `READ/DATA` issues on the last port (`qubic.bas`).
-   Changed  `RND`  to  `RND(1)`.
-   Corrected  `150`  to the winning square  `158`.
-   Corrected the machine-search direction from  `T=T1-K`  to  `U=U+K`.
-   Corrected the diagonal legality equation.
-   Repaired the duplicate line 3340.
-   Prevented  `GOSUB`  and  `FOR`  stack leaks.
-   Added complete board-coordinate validation.
-   Corrected the no-instructions branch to print only the board.
-   Renumbered the invalid  `99999 END`  to  `9999 END`.
