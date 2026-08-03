# mnopfl.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

On it's own, this program was intended to create two data files required by `mnoply.bas`, which is the actual game program.

Since we generally do not have file storage on Ben Eater 6502 builds, this is not a particularly useful program; however, I ported it anyway, for the sense of "completeness" as a discrete program, and also as a precursor to include as part of my port of `monply.bas` so that the game part would actually be playable.

See `mnoply.md` for more details.

## OCR/Transcription Corrections

The property-name array was incorrectly transcribed as `Q$(40)` instead of the original `G$(I)`.  This wouldn't matter much, but we want to use it later for the game, so this was corrected to be a value the game program, `mnoply.bas` expects.

`MATLIDA'S MONOPOLY` was corrected to `MATILDA'S MONOPOLY`.

And the original title record, on line 200, was truncated slightly so as not to exceed line-length limits if moved to a 4-character line number when incorporated into the second part of this port.

## Porting

Variations source-dialect abbreviations/symbols (e.g. `!` for `REM`) were replaced with their MS-BASIC equivalents, and I removed the source type annotation suffixes.

All file operations were removed.

Data is now stored using normal in-memory arrays instead of on disk files.

In an earlier conversion, with lots of data, I found that sometimes the `DATA` pointer didn't start on the first element, and could result in "out of data errors", so a precautionary `RESTORE` is issued here before reading anything.

And then, because this program doesn't **do** anything with this data itself, I simply added a completion report so the standalone program visibly confirms that all data was loaded.
