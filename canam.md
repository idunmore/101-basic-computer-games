# canam.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

This program was originally written to allow simultaneous multi-player gameplay using separate terminals for each player on a Honeywell/GE 635.  There is no way to recreate this on a single BE6502 running MS-BASIC, so the game has been modified to be single player against multiple computer drivers.

*The comments in the original relating to multi-terminal/player support have been removed, which reduces the listing length, as does the simpler implementation.*

This means substantial aspects of the program were re-written/replaced, and being unable to run the original means there's a good chance some of that is not accurate to the original (even given the above limitations).

## OCR/Transcription Corrections

There were simple, and typical, errors in the OCR/transcription, such as `Y4=H(G)` which should be `Y4=T(G)`.  `Q$(Z)` was transposed with `O$(Z)`; both appear in the original listing, but they are used for different things (player names vs. terminal routing "command" strings).

Line 3060 was incorrectly used as a `GOTO` target when rain begins, which results in a "next without for" error; this was changed to the correct line, 3080.

Relational operators were modified to match the original, so `S>=20` instead of the erroneous `S=>20`.

## Porting

A number of keywords/functions and capabilities exist in the original dialect of BASIC this was written for, so these were either removed (if not needed, e.g, `RANDOMIZE`), or alternative implementations were used.  Specifically, `TAB()`, `MAT`, `CHANGE` and function definition via `DEF FN` were replaced with inline code or other routines.

Changes to the way the circuit/track is drawn, including replacing the terminal-specific character code 127 with standard ASC-II 57.

Due to the inability to run the original code, and not being familiar with the machine in question, I used **AI** (specifically OpenAI Codex, Sol 5.6 on high-effort) to rework the multi-player and display logic.

Codex used `_` (underscore) characters to draw some parts of the track, but when pasting the listing into MS-BASIC (since the BE6502 lacks a way to load files from other media currently) the input routine interprets `_` as a BACKSPACE and thus removes previously entered characters.  This was fixed simply by changing those characters to `-` (minus) instead; doesn't look quite as good but its a simpler fix than inlining `CHR$()` output calls in already fiddly code.
