# qubic.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

A good number of errors in the OCR or AI-assisted transcription had to be corrected:

-   Corrected the title from  `CUBIC`  to  `QUBIC`.
    
-   Corrected the line-table loader:
    
    -   Outer loop variable changed from  `J`  to  `I`.
    -   Inner loop retained  `J`.
    -   Corrected the corresponding  `NEXT`  variables.
-   Corrected coordinate decoding:
    
    -   `J2=INT((J1-K1*100)/10)`  became  `J2=J1-K1*100`.
    
-   Restored the missing successful branch after checking whether a square was empty.
    
-   Corrected the three-pass strategy scan where both loops had been transcribed with variable  `J`; the inner scan uses  `I`.
    
-   Corrected the machine-winning total from  `14`  to  `15`.
    
-   Corrected  `P=P*X(M(I,J))`  to  `P=P+X(M(I,J))`.
    
-   Corrected  `L(I)=5`  to  `X(M(I,J))=5`.
    
-   Corrected the nonexistent  `GOTO 1628`  target.
    
-   Corrected the damaged expression at line 1705 to:
    
```
1705 IF I-INT(I/4)*4>1 THEN 1715
```

-   Corrected the candidate comparison from  `X(M(I,J))=5`  to  `X(M(I,J))=S`.
-   Corrected the strategy branch from line 1410 so it does not reset  `S`.
-   Restored the omitted temporary-marker cleanup:

```
1815 LET X(I)=0
```

-   Corrected the truncated DATA values:
    
    -   The final  `3`  on line 1520 became  `38`.
    -   The final  `5`  on line 1521 became  `56`.


## Porting

I ran into a very odd issue, in which the second `READ` loop (lines 24 through 28) would throw an "out of data" error.  The number of data items is correct, so this didn't make sense.

More out of trial and error than anything else, I put a `RESTORE` statement on line 19 and that fixed it.

I don't know if that means there are situations in which this version of MS-BASIC does not reliably start reading data from the first value in the first `DATA` statement, or if this was a result of running the programming previously and something not getting reset, but the `RESTORE` fixes it.

The `NO` to instruction branch was updated to start with line 19 as a result.

`FOR/NEXT` loops that were exited prematurely were replaced with counter-loops to preserve the state of the stack correctly.

Updated the case where there are two `FOR/NEXT` loops, both sharing a single variable (since MS-BASIC does not support "local" variables, nor any kind of block or other scope control).
