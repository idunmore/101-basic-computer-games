# tower.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

There were a few cases of OCR/transcription error here.

The most significant was interpreting the number `7` in `FOR/NEXT` statements as `?` ... which MS-BASIC interprets as a shortcut for `PRINT` (which it then expands) - something I didn't know until tackling this particular program.

The rest were minor expression errors that immediately threw syntax errors, so were easy to find and correct.

Oddly, the other "7"s in the file were interpreted correctly ...

## Porting

This one was both fun and a bit frustrating.

Lines longer than 72 characters (MS-BASIC's line-length-limit) were split onto additional lines.

The primary array `T` was originally dimensioned as 7, 3, but the logic indexes outside of those bounds and causes errors, so I increased the size of the array.

Game replay logic originally jumped to where the array is `DIM`ensioned, which causes an error for MS-BASIC, so I changed the replay `GOTO` target to 115 and added a line to zero out the array there.

*Strictly* speaking, line 115 shouldn't be necessary as lines 130-170 then zero out the elements of the array that *should* be all that's needed, but after several dozen test-runs with this in place, I didn't feel like repeating them after removing it; so if you're curious `REM` out line 115 (you need to keep "a" line 115) and see what happens!

The hardest part of this one was the `PRINT`/output routine for showing the towers and the discs.  The original code uses the `TAB()` modifier for layout, but the MS-BASIC version doesn't seem to work like any other candidate source BASIC's `TAB()` function.

After an unreasonable amount of time trying to figure out how to minimally alter that code to get the right result, I'd had enough and simply re-wrote the code that outputs the towers and discs entirely.  
