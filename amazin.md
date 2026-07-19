# amazin.bas

This file required adjustments to the code as part of porting it.

**Note:** The program uses more memory than the standard Ben Eater 6502 build has available.  This is down to the size of the maze arrays defined in line 110:

````
110 DIM W(25,103),V(25,103)
````

This will generate an `OUT OF MEMORY ERROR`.

To actually run the program, **you** will want to change line 110 to something like this (I haven't exhaustively tried to figure out the maximum dimensions possible):

````
110 DIM W(30,30),V(30,30)
````

*I **deliberately** didn't make the above change in the code as I want to preserve as much of the original as possible.*

When prompted for the `WIDTH` and `LENGTH`, make sure the numbers are smaller than the values in the above `DIM` statement.

Also, maze generation outputs the first line very quickly, and then depending on the size of the maze it can take a while it starts to output the rest of it, so be patient; a 20x20 maze may take a minute or two.

If you get a `BAD SUBSCRIPT ERROR`, try reducing the numbers you enter for the width and length.
## OCR/Transcription Corrections

**None.**

## Porting

The unsupported command `RANDOMIZE` was removed (line 100), and all references to  `RND(0)` were changed to `RND(1)`, since `RND(0)` will always generate the same number for a given run in the target version of MS-BASIC.
