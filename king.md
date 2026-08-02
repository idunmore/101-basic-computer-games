# king.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Lots of little changes, some with game-breaking impact:
-   Line 34:  `MAGNIFICIENT`  to  `MAGNIFICENT`.
-   Line 50: initial treasury  `64000`  to  `60000`, and restored the missing closing parenthesis.
-   Line 310: corrupted  `A(HW)`  expression restored as  `A+H*W`.
-   Line 1170: removed an extra closing parenthesis in the funeral-cost calculation.
-   Line 1189: land forced to be sold at  `A/4`  to  `A/W`.
-   Line 1224:  `C>=0`  to  `C>0`.
-   Line 1250: incorrect  `+(2000-D)/50`  to  `-(2000-D)/50`.
-   Line 1290: population was mistakenly assigned to  `H`; corrected to  `B=B+P1`.
-   Line 1305: pollution calculation used worker count  `C`; corrected to land value  `D`.
-   Line 1500: excessive-deaths threshold  `230`  to  `200`.
-   Line 1520: literal  `5`  to year counter  `X5`.
-   Line 1730: malformed  `G OTO`  to  `GOTO`.
-   Ending text: recombined the broken  `NEVER THE`  /  `LESS`  wording as  `NEVERTHELESS`  and corrected  `GOODBY`  →  `GOODBYE`.

## Porting

- Removed  `RANDOMIZE`  as it isn't supported nor necessary.

- Split lines >72 characters onto multiple lines, to start under MS-BASICs line length limit.
