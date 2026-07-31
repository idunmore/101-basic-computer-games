# life.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

These were primarily array-subscript and variable name issues, with a couple of cases of using `,` as a separator.

## Porting

Removed the trailing `%` characters from all of the variables and literals where they were present.

Adjusted logic for line 590 to accommodate the unsupported `ELSE` clause.

Replaced the `LINE` based (keyboard-as-file) input routine with a line-by-line (row-by-row) `INPUT` loop; entries need to be enclosed in double-quotes to preserve leading spaces (otherwise they are trimmed).  Row entry concludes by entering "DONE", rather than relying on an input error (via `ON ERROR`).

And then replacing the `TAB()` modifiers behavior with a cursor-position tracked absolute spacing routine.
