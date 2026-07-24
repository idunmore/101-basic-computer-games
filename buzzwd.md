# buzzwd.bas

This program required  **both**  corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

I only encountered one OCR/transcription error; the line number for line 1080 had been OCRd/transcribed as 1082.  Since line 1080 is a `GOTO` target, this caused an error.

## Porting

Statement separators were changed from  `\`  to  `:`.

Line 1310 was removed due to the unnecessary, unsupported, command `CHAIN "DEMON"`.
