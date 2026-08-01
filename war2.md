# war2.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

These were limited to replacing the `,`  at the ends of the `PRINT` statements on lines 9 and 11, so that the `INPUT` requests all occurred on the same line as the prompt.

## Porting

This was primarily down to switching abbreviations for `PRINT` (`PRI`) and `GOTO` (`GOT`) to the full MS-BASIC keywords.

I also slightly adjusted the `PRINT` call on line 6, adding an extra `,` to get the text there to line up correctly.  And then a similar change on line 501.

For line 501 I also added extra spaces in front of `YOU` and `ME` to make them align properly.  The original code is off by one character, perhaps deliberately, but it was bugging me so I "fixed it".
