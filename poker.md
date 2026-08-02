# poker.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

*I had Codex look at the diffs and produce the change lists, below, as there were so many fiddly little changes that I stopped keeping notes.*

## OCR/Transcription Corrections

-   Corrected “CARDS SO YOU WANT” to “CARDS DO YOU WANT.”
-   Corrected  `LET$S=H$`  to  `LET J$=H$`.
-   Removed the stray semicolon from  `GOSUB 195;`.
-   Restored missing closing parentheses in arithmetic expressions.
-   Corrected an inner  `NEXT I`  to  `NEXT K`.
-   Corrected  `IF K=9`  to  `IF K>=9`.
-   Corrected  `IF G>5`  to the intended boundary comparison where applicable.
-   Corrected  `3+Z`  to  `3*Z`.
-   Reconstructed the malformed comparison at line 348.
-   Corrected several occurrences where the variable  `O`  had been transcribed as zero.
-   Restored the omitted non-flush tie comparisons.
-   Restored the missing drawn-hand message and preservation of the pot.

## Porting

-   Removed the unsupported  `RANDOM`/`RANDOMIZE`  statement.    
-   Standardized random-number calls as  `RND(1)`.    
-   Increased  `A(15)`  to  `A(16)`, since the program can store as many as 16 cards while processing both draws.    
-   Rewrote the duplicate-card search at lines 173–184 without a  `FOR`  loop. This avoids:    
    -   executing an empty loop once in this MS-BASIC;
    -   indexing outside the array;
    -   repeatedly abandoning active  `FOR`  frames and exhausting memory. 
-   Corrected the duplicate-card search bounds so a newly generated card is compared only with existing cards.    
-   Replaced the win/fold handler’s  `GOSUB 65`  calls with ordinary branches. The handler restarted at line 12 without executing  `RETURN`, leaking one return-stack entry per affected hand and eventually causing “OUT OF MEMORY” at unrelated lines such as 195.
