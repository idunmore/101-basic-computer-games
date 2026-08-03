# stock.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

-   Line 101: revision year  `8/18/78`  should be  `8/18/70`.
-   Lines 102–108: several numeric variable names were mistaken for strings:
    -   `B$`  corrected to  `B5`
    -   `P$`  corrected to  `P5`
    -   the two  `S$`  corrected to →  `S4`  and  `S5`
    -   `T$`  corrected to  `T5`
    -   `W$`  corrected to  `W3`
-   Line 113:  `RANDOMIZE`  should have been  `LET X=1`.
-   Line 114:  `*100.5`  should be  `*100+.5`.
-   Line 115:  `T$=0`  should be  `T5=0`.
-   Line 126:  `Z9<>1`  should be  `Z9<1`.
-   Line 358:  `CENSORED BOOKS STORE`  should be  `CENSURED BOOKS STORE`.
-   Line 391: parentheses were misplaced and one was missing. The correct calculation is:  
    `Z5=INT(100*(Z5/5)+.5)/100`
-   Line 395:  `IF X9=0`  should be  `IF X9>0`; the error reversed when the net change was displayed.
-   Line 580:  `Z(I)<0`  should be  `Z(I)<=0`.
-   Line 656:  `C5<0`  should be  `C5>=0`. This reversed the available-cash test.
-   Line 658: a semicolon was missing after  `-C5`.
-   Lines 266, 845–846, 855–856 and 990:  `+1`  belonged inside the  `INT()`  parentheses. This did not materially change the result.
-   Line 949:  `W3=-10`  should be  `W3=W3-10`, allowing simultaneous positive and negative special changes to cancel.
-   Line 955: the stock-change expression was malformed and missing a parenthesis.  `X1`  is an additive fractional change, not a multiplier:  
    `C(I)=INT(A*S(I))+X1+INT(3-6*RND(X)+.5)+W3`
-   Line 994:  `S4<.5`  should be  `S4<=.5`.

## Porting

-   Corrected calculations and reversed conditions.
-   `RND(1)`  throughout; no  `RANDOMIZE`.
-   Literal spacing instead of  `TAB()`.
-   Stack-safe transaction validation.
-   `CHR$(7)`  for the bell.
