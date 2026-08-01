# dogs.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

There is a significant variation in one aspect of my ported version of this and the original; the original uses file I/O to keep persistent records with are carried over from game to game, where as MS-BASIC on the BE6502 does not have persistent I/O support nor storage.

So here, the code generates 25 "historical" races and then keeps the stats update for all the races played in that session.  If you exit and re-run the game, a new set of 25 prior race results will be generated; they are not stored persistently.

## OCR/Transcription Corrections

Several variable names for `FOR/NEXT` loops, calculations and some logic that resulted in unreachable code (win/loss updates), had to be corrected.

## Porting

- Changed the statement separators from `\` to `:`.

- Replaced `RND(X)` with `RND(1)` to get the syntactically and behaviorally correct output in MS-BASIC, and removed the `RANDOMIZE` calls.

- `TAB()` modifier was replaced with fixed spaced output.

- `RECORD`, `GET`, `PUT`, `UNSAVE` were removed as part of switching to an in-memory, non-persistent, race history table.

- Removed special terminal characters, and replaced them with the larger "FINISH" banner instead.
