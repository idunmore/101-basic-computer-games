# mnoply.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

I left this one until last on purpose.  This was a two part program, with the original version using `mnopfl.bas` to create a pair of data files needed by `mnoply.bas` (this program) in order to play.

This meant to make this game playable, it would have to incorporate both programs into a single game.  And making all of these original listings playable *is the whole point* of this project.

Instead of using file-storage, which we don't have, the two programs have been ported individually, and then the work on the first incorporated into this one, so it has all it needs to be playable.

See `mnopfl.md` for details from the perspective of the "other" program.

*Effectively, the entire of `mnopfl.bas` data, starting from line 100, has been copied into `mnoply.bas` but starting at line 40000.  Since `READ` statements don't care about line numbers, this is an easy way to reuse the ported `mnopfl.bas` code in `mnoply.bas` without having to do a wholesale renumbering on `mnoply.bas`!*

## OCR/Transcription Corrections

There are a good number of them, though based on looking at the printed listing, it could have been far worse!

-   Line 7 incorrectly declared the fourth property-file array as  `H%(40)`. It needed to be the rent array  `R(40)`;  `H%`  was already the local house-count array.
    
-   Line 100 had  `";S TURN"`  instead of the possessive  `"'S TURN"`.
    
-   Line 200 used  `NS(2)`  instead of  `N$(2)`.
    
-   On line 1000, a  `!`  before  `RANDOMIZE`  turned the entire dice routine into a comment.
    
-   Lines 2010–2012 used  `!`  where statement separators were required, commenting out important  `RETURN`  and position-update statements.
    
-   Line 2026 was missing the closing quotation mark after  `DOLLARS`.
    
-   Lines 2127 and 2128 had missing closing parentheses in  `R(I(Z))`.
    
-   Line 3170 contained the malformed assignment  `C,D:=0`.
    
-   Line 3212 had  `OSUB 3262`  instead of  `GOSUB 3262`.
    
-   The pink property group advertised houses at $100 each but charged only $150 for all three properties. The total was corrected to $300.
    
-   Several card actions contradicted their printed instructions:
    
    -   Paying poor tax added $15.
    -   Doctor, hospital, and school charges added money.
    -   “Go back three spaces” moved forward three spaces.
    -   Some jail cards awarded $50.
    -   Passing GO deducted $200.
-   The original player-two rent code was unreachable because player one’s rent message and  `RETURN`  occurred first.

## Porting

There was quite a lot to do, here, also, though a good portion is a result of not reading the initialization data from files and, instead, pulling it from the internal `DATA` statements.

-   Removed  `OPEN`,  `CLOSE`, and mapped-file  `DIM #`  statements.
    
-   Embedded all property, message, Chance, and Community Chest records as  `DATA`.
    
-   Added  `RESTORE`  and initialization loops to load everything into memory.
    
-   Various abbreviation and suffix adjustements/removals, including  `!`   to  `REM` , removing end-of-line comments, swapping `&`  output statements with  `PRINT` and removing all  `%`  integer suffixes.
    
-   Expanded RSTS multiple assignments into ordinary MS-BASIC assignments.
    
-   Removed  `RANDOMIZE`  and changed random calls to  `RND(1)`.
    
-   Replaced the long dice-selection chains with  `INT(RND(1)*6)+1`.
    
-   Replaced the  `DEF FNR`  rent function with direct rent calculation.
    
-   Reworked conditional flow as our target version of MS-BASIC skips the entire remainder of the line on a condition that evaluates to `FALSE`.
    
-   Replaced property-list loops with manual counters so an empty list does not execute once (this is probably the most prevalent "true porting" aspect of all the changes in all the listings, as it broke so many of them as-is), closely followed by:
    
-   Avoided jumping or returning out of active  `FOR`  loops.
    
-   Consolidated the eight color groups into in-memory tables containing:
    
    -   House price
    -   Number of properties
    -   Board positions belonging to the group
    
-   Added validation for the  `ROLL`  command and negative house purchases.
