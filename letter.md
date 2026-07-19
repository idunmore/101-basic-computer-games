# letter.bas

This file required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

 Three types of change were required to the original code:

- Removing unsupported commands (e.g., "`RANDOMIZE`", line 90, which is neither supported nor necessary).    
  
- Syntax/argument changes for supported constructs (e.g., "`RND(0)`" needs to be "`RND(1)`"), and multi-statement lines (changing "`\`" to "`:`").

- A logic change on line 430 to take input as a string (since it is a character), and then convert it to a numeric value via "`ASC()`" for comparison on line 435.