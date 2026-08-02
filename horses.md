# horses.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

-   Restored the horse-speed formula’s missing zero:  `1000+50*O(I)`.

-   Removed the duplicated, corrupted race-header line.

-   Reconstructed the damaged mutuel calculation and digit formatter.

-   Removed the stray  `k`  after  `COALTOWN`.

## Porting


-   Replaced  `TAB()`  with explicit two- and three-space column alignment.

-   Replaced  `SLEEP`  with a compatible delay loop.

-   Removed  `RANDOMIZE`  and changed random calls to  `RND(1)`.

-   Converted all  `\`  separators to  `:`.

-   Separated affected compound  `IF`  statements.
