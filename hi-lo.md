# hi-lo.bas

This file required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Line 280 OCR'd/transcribed as: `280 PRINT "IF B<6 THEN 200`, instead of: `280 PRINT\IF B<6 THEN 200`, which is a syntax error.

## Porting

 Two types of change were required to the original code:

- Removing unsupported commands (e.g., "`RANDOMIZE`", line 90, which is neither supported nor necessary).    
  
- Syntax/argument changes for supported constructs (e.g., "`RND(0)`" needs to be "`RND(1)`"), and multi-statement lines (changing "`\`" to "`:`").
