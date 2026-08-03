# animal.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

This program was originally written to store the animals it knew, and could guess, in an external text file.  It had two built-into the code, but was otherwise reliant on an "animal.gme" file (described in the book).

*Since typical Ben Eater 6502 builds do not have any kind of file system or persistent storage, this meant changing the way the game works.*

To make this more interesting, my conversion here includes 16 animals built into the code, rather than the original 2.

Like the original program, it can also learn (upto 34) new animals.  However, these only last for the duration of the "run" (until you exit the game or restart BASIC) since we don't have a way to persist them.

As such, this is a substantial update/partial re-write of the original.  It plays the same, looks the same, but is a bit different under the hood.

## OCR/Transcription Corrections

-   Line 100 was missing the closing quotation mark after  `RSTS`.

-   Line 2200 stored a newly learned animal as  `Z9$`. It should have included the animal marker:  `"\A"+Z9$`. Without it, learned animals would be truncated when displayed and omitted from  `LIST`.

-   Line 12400 was almost certainly an extra-digit transcription of line 2400. The destination itself worked, but the numbering was inconsistent with the surrounding listing.

## Porting

- Replaced all the file operations with in-memory DATA records, adding 14 new built-in animals (for a total of 16).

- Replaced RSTS BASIC `&` abbreviations for `PRINT` with normal MS-BASIC `PRINT` calls.

- Adjusted conditional constructs and statement structure to work around MS-BASIC not supporting the RSTS `ELSE` clause for `IF` statements.

- Replaced `INSTR()` (which is unsupported) with simpler numeric YES/NO branches.
