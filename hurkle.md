# hurkle.bas

This file required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

Some OCR/transcription errors had already been fixed (and are commented as such in the code).

## Porting

 Two of types of change were required to the original code:

- Removing unsupported commands (e.g., "`RANDOMIZE`", line 5, which is neither supported nor necessary).    
  
- Syntax/argument changes for supported constructs (e.g., "`RND(0)`" needs to be "`RND(1)`").

  Switching "`\`" to "`:`" when chaining statements on the same line.

## Learning

I had previously thought that the version of MS-BASIC I am porting to did not support multi-statement lines; it **does**.

Statements are separated by a colon: "`:`".

The "101 BASIC Computer Games" use "`\`" instead, so that must be converted.

However, this makes compound statements much easier to port as they do not require changes in logic/flow and/or additional lines of code to compensate.
