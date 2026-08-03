# spcwar.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## spcwar.bas vs. spcwar-16k.bas

I've made two ports of the original `spcwar.bas` here.  The gameplay is the same, but the "full" original version requires more memory than most BE6502 builds will have (24KB vs. the stock 16KB):

- **spcwar.bas** - This is the full port, and requires 24KB of RAM to run.

- **spcwar-16.bas** -  This version will run on a 16KB machine; the instructions were moved out of the main game and into a separate markdown file (`spcwar-16k-instructions.md`)

Otherwise, the correction and porting issues were the same for both versions:

## OCR/Transcription Corrections

-   Added the missing  `D(8)`  damage-array declaration.
-   Corrected  `MINO REVISIONS`  to  `MINOR REVISIONS`.
-   Restored the missing integer course index:
    -   `C2=INT(C1)`
    -   Course-vector calculations now index  `C(C2,...)`, not  `C(C1,...)`  when  `C1`  is fractional.
-   Corrected course validation from  `C1>9`  to  `C1>=9`, preventing access to nonexistent row  `C(10,...)`.
-   Removed the duplicated  `X1`  calculation at line 1860.
-   Restored missing  `+.5`  coordinate rounding when:
    -   Finishing a warp move.
    -   Entering a new quadrant.
    -   Locating a Klingon struck by a torpedo.
    -   Removing an object from the sector strings.
    -   Comparing sector-string positions.
-   Restored the missing  `C2=INT(C1)`  in the photon-torpedo routine.
-   Restored the omitted “PHASER CONTROL IS DISABLED” message.
-   Corrected the no-Klingon/no-starbase safeguard. The galaxy should be regenerated, not overwrite  `G(6,3)`  with  `114`.
-   Decremented both  `B3`  and the galaxy-wide  `B9`  when a starbase is destroyed.
-   Restored the missing  `H8=1`  calculator-mode flag. Without it, the calculator could fall into a  `NEXT`  without an active  `FOR`.
-   Corrected device-name extraction from 11 to 12 characters.
-   Corrected minor text errors such as  `NAVAGATION`,  `SENSON`,  `PERTINATE`,  `ENERY`, and  `TEMPORARALY`.

## Porting

-   Removed unsupported and unnecessary  `RANDOMIZE`.
-   Changed exponentiation from  `**`  to  `^`.
-   Replaced  `MAT ...=ZER`  with ordinary initialization loops.
-   Split chained assignments into MS-BASIC-compatible statements.
-   Added  `THEN`  to conditional branches where required.
-   Replaced  `MID`,  `LEFT`, and  `RIGHT`  with compatible  `MID$`  and  `LEFT$`  operations.
-   Rewrote substring replacement because MS-BASIC’s  `RIGHT$()`  means “rightmost characters,” not “substring beginning at this position.”
-   Replaced every  `PRINT USING`  display with direct printing routines.
-   Added a three-digit output routine for long-range scans and galactic records.
-   Rebuilt the short-range scan without formatted-print support.
-   Removed  `TIME(0)`  and the real-world mission timer.
-   Constructed the 72-space sector buffer in stages rather than putting an oversized literal on one line.
-   Rewrote zero-count Klingon, starbase, and star loops because this MS-BASIC executes a  `FOR`  loop once even when its initial limit is already exceeded.
-   Rewrote movement, phaser, torpedo, attack, and docking-search loops to prevent jumps from abandoning active  `FOR`frames.
-   Changed the Klingon attack subroutine to return a destruction flag instead of jumping out without  `RETURN`.
-   Moved  `DIM`  and  `DEF`  ahead of the restart point, avoiding re-execution of  `DIM`  on subsequent games.
-   For the 16K edition, removed the embedded manual and nonessential remarks. The instructions are supplied separately, reducing the listing from 18,425 to 13,500 characters.
