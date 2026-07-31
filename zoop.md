# zoop.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

The original reads key presses without needing an "Enter" action.  When it receives valid keypresses it converts them to a single value (line 120) and then uses that to dispatch the appropriate "command".

It took a while to figure out what was going on, not being familiar with the original BASIC compiler being simulated.  Once I did, things changed into a more "invasive" change than I think would be ideal.

The easiest path to porting, which results in rather different code, was to revert to using `INPUT`.   This means an "Enter" action is required to process a "command", and as a result the original `PRINT` statements that show the command's characters AFTER the two entered were adjusted to print the entire command (since it is now on a new line), and the original response.

Newly-irrelevant code was `REM`med out.

`CHAIN` (which would load the specified program on the original systems) is replaced with a "restart".
