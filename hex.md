# hex.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

This is the 89th program I've converted as part of this project; and only the third (I think) that I've used AI assistance for.  I got as far as I could, and at the point I was just reading what I *thought* was there, rather than *actually* there, I invoked Codex to try and finish it.

Even that required multiple iterations with my steering input, and I still had to determine why some things were causing errors in order to get Codex to affect a fix (e.g., it tried variations of `INSTR()` over multiple iterations, until I pointed out that this version of MS-BASIC does not support `INSTR()`).

## OCR/Transcription Corrections

There's a list ... some of which I swear I looked "through" several times, but missed:

-   Corrected the initial board from  `"****---OOO"`  to  `"***---OOO"`—three computer pawns, three empty squares, and three player pawns.
-   Restored the corrupted position-table lookup:
    -   `C%=PS(C%)`  to  `C$=P$(C)`
-   Corrected several string-variable transcription mistakes:
    -   `MS`  and  `MS$`  to  `M$`
    -   Numeric  `B$`  to  `B`
    -   Numeric  `K%`  to move string  `K$`
-   Restored the missing/misnumbered portion of the move-generation routine, including the second diagonal-capture test.
-   Corrected the incomplete instruction text  `"O THE BOARD"`  to  `"ON THE BOARD"`.
-   Reconstructed statements that had been split incorrectly across printed lines.

## Porting

Changes here were extensive, even given the relatively short size of the listing (well, it *looks* short until you start expanding the single-character keyword abbreviations):

-   Converted  `!`  comments to  `REM`.
-   Replaced BASIC-PLUS  `&`  printing shorthand with  `PRINT`.
-   Replaced  `\`  statement separators with  `:`.
-   Removed integer  `%`  suffixes.
-   Removed the unsupported  `RANDOMIZE`  statement and used  `RND(1)`.
-   Replaced BASIC-PLUS multiline  `DEF`/`FNEND`  string functions with ordinary MS-BASIC expressions.
-   Replaced  `NUM$()`  with  `CHR$()`  for converting square numbers to characters.
-   Converted BASIC-PLUS  `RIGHT$(string,start)`  operations to the equivalent  `MID$()`  operations.
-   Rewrote postfix  `IF`  statements and  `ELSE`  constructions into compatible branches.
-   Replaced every unsupported  `INSTR()`  call with a substring-search subroutine using  `MID$()`,  `LEN()`, and a loop.
-   Split long statements so every source line remains within the 72-character limit.

A lot of line-shifting/renumbering was necessary to fit in accommodations for things MS-BASIC doesn't support (or that work differently).
