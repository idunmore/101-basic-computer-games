# salvo1.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

The issues here were primarily around line numbers and lines being duplicated.

Line 350 in the original listing is:

````
FOR R=1 TO 10\PRINT\NEXT R
````

The OCR/transcribed version corrupted line 350 and added a phantom line 360:

````
350 FOR R=1 TO 10
360 PRINT "NEXT R
````

Then the routine starting at line 710, which assess whether the player has hit one of the computer's bases, didn't transcribe lines 820 and 860 and instead replicated line 780 three times (which, when pasted into MS-BASIC, results in ONE line 780).

This resulted in you winning the game when you hit the computer's second base, as it just falls through the evaluation and executes all the cases.

So, this was corrected to be:

````
770 PRINT " ONE DOWN THREE TO GO"
780 PRINT:PRINT:GOTO 570
810 PRINT " TWO DOWN TWO TO GO"
820 PRINT:PRINT:GOTO 570
850 PRINT " THREE DOWN ONE TO GO"
860 PRINT:PRINT:GOTO 570
````

## Porting

Statement separators were switched from `\` to MS-BASIC compatible `:`.

`RANDOMIZE` was removed and `RND(N)` calls were replaced with `RND(1)`.
