# ugly.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

A lot of the issues encountered are **extremely** hard to read in the original printed listing.  In fact some characters, such as the presence/absence of some `;` at the ends of `PRINT` statements, had to be determined by trial and error.

Remaning issues were some line number errors, and the character `7` being interpreted as `?`, which MS-BASIC expands to `PRINT` and causes a syntax error (`327 IF F=PRINT THEN 323`).

## Porting

`REM`med out the `RANDOMIZE` statement on line 9, and changed the single `RND` references to `RND(1)` to get correct syntax and the desired random number generation behavior.

Changed `\` statement separators to `:`.

Replaced the `TAB()` modifier with a naive subroutine alternative, that simply prints the number of spaces specified in `TB`.

This approach works when always starting from the first character position on a line, but it has no knowledge of the position of the cursor when called, so would not be appropriate as an alternative to most source BASIC `TAB()` implementations:

- Some source BASIC dialects implement `TAB(n)` as "move to column *n*, if the cursor has not already passed it".
-  Others implement it as "move to TAB position `n`" , where tab size is set with a `WIDTH` keyword,  if the cursor has not already passed it".
- And others move it (relative) `n` TAB positions regardless.

MS-BASIC *seems* to observe the 2nd pattern, but it doesn't work correctly on the BE6502 serial output, as any value <14 does nothing, and after that it is almost random.
