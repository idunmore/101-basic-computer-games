# rockt1.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Corrected the calculation `H=H-5*(V+V1)` to `H=H-.5*(V+V1)` (the error causes 10x the decent rate at the start).

Fixed a typo from the original listing that was *correctly* transcribed (so still an error); "BUT YOU SECOND-BY-SECOND" to "BUT YOUR ...".


## Porting

- Changed the statement separators from `\` to `:`.

- `TAB()` modifier was replaced with fixed column output and a spacing loop.

- My first spacing-loop implementations fell foul of MS-BASIC always executing the code in a `FOR/NEXT` loop **at least once**, even if the exit condition is always met; guard/pre-checks occur to prevent this (which was shifting the display for double-digit turn numbers, etc.).
