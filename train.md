# train.bas

This file required  **both**  corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

A single transcription error, on line 50, results in the original:

````
50 E=INT(ABS((V-A)*100/A)+.5)
````

being transcribed as:

````
50 E=INT(ABS((V-A)*100)/A)+.5)
````

Which yields a syntax error, due to the extra parenthesis.

## Porting

Basic changes were necessary to make  `gomoko`  run:

The  `RANDOMIZE`  call was removed as it is neither supported nor necessary. Also, the calls to  `RND`  were replaced with  `RND(1)`  as that is the MS-BASIC equivalent.

The multi-statement separator  `\`  was replaced with ':'
