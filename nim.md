# nim.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

-   Line 425 contained a stray period before  `X(I,Y)`.
    
-   Line 455 had a malformed chained comparison:
    
    ```
    IF V(Y)/2=INT(V(Y)/2)=0 THEN 480
    ```
    
    The final  `=0`  was erroneous. The test should simply detect an even binary-column total.
    
-   Line 540 used  `D#1`, which both had the wrong operator for MS-BASIC and selected the wrong singular/plural message. The intended test is:
    
    ```
    IF D=1 THEN 550
    ```

## Porting

-   Replaced  `\`  statements separator with  `:`.
    
-   Changed active line 190 from illegal  `RANDOM`  to  `REM RANDOM`.
    
-   Initially converted random calls to  `RND(1)`,  but then ran into an issue where randomly looking at remaining items could wind up in an infinite loop (or effectively seem like that due to it taking innumerable iterations to hit the necessary values).

    So I replaced the random retry loops with deterministic pile scans after they repeatedly stalled in this BASIC.
    
-   Split statements as required to keep every physical line under 72 characters.
    
-   Separated compound  `IF`  statements onto individual lines. In this MS-BASIC, a false  `IF`  skips the entire remainder of its physical line, so constructs such as:
    
    ```
    IF P>INT(P) THEN 215:IF P<=0 THEN 215:GOTO 220
    ```
    
    rejected every valid pile count.
    
    There were several of this type of setup, so corrections were made throughout the input validation, board display, binary conversion, and computer-move routines.
    
-   Changed the end-of-game entry at line 270 to recalculate the total directly from the pile array before testing for zero. This prevents a stale running total from requesting another move after all sticks are gone.
