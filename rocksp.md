# rocksp.bas

This file required multiple adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

Spelling errors in some of the strings are present in the listing as presented in the original book.

## Porting

Three major types of change were required to the original code:

- Removing unsupported commands (e.g., "`RANDOMIZE`", line 5, which is neither supported nor necessary).    
  
 - Correcting invalid syntax/function calls (e.g., line 20,
    "`X=INT(RND*3+1)`", becomes "`X=INT((RND(1)*3)+1)`".
    
 - And the most frequent and "complicated", changing multi-line
    statements (lines that have "\\" characters separating statements)
    into several discrete lines.
        
    In most cases these were sequential PRINT statements (to add a blank line).  However, line 32 was trickier; here, the logic had to be inverted (`=0` instead of `<>0`), and then either fall-through for an invalid selection, or `GOTO` for a valid selection to skip the retry code.

Fortunately, while the changes required adding a number of lines of code, no original line numbers had to be *renumbered*; there were enough "free" lines between line numbers to add the required additional lines.
