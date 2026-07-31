# boat.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

A good number of the variable names and computational expressions are very hard to read in the original listing and were incorrectly OCRd/transcribed.

Fixing them required not just reading the original listing but some logical deduction as it was not possible to make out, reliably, all of the variable names there.

## Porting

Minimal work required here; just removing `RANDOMIZE` calls (not supported, nor necessary), changing `RND(0)` references to `RND(1)` to get a varying random result, and then splitting some of the `PRINT` lines so they would be shorter than the maximum-line length of 72 characters.
