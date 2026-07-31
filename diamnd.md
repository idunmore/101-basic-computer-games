# diamnd.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

On line 35 the `PRINT` statement was converted as `PRINT " "` where the original listing shows `PRINT "!"`.

## Porting

The principal change here was to the `PRINT` routine.  This made use of the `TAB()` modifier, which doesn't behave like any of the source BASIC dialects.

So the `PRINT` behavior was re-written to work without `TAB()`.
