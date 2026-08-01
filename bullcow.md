# bullcow.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Corrected comparison operators to match the proper bounds, added missing semicolons, and changed line 340's `FOR/NEXT` loop to have the correct end value (`4` instead of `P`).

## Porting

Removed the `GOSUB` on the first line; there is no `RETURN` in the original listing, instead it just `GOTO`s back to line 10, and replaced it with a `GOTO`.

Changed the restart point to avoid redimensioning arrays.

Removed the unsupported, and unnecessary, `RANDOMIZE` statements.

## Gameplay

It is worth noting that the computer can spend a fair bit of time thinking for when it guesses; tens of seconds isn't uncommon, and sometimes it can be a minute or more.
