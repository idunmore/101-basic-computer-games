
# gomoko.bas

This file required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

The original scan of the book for this program is **very** hard to read.  Surprisingly, I only found two errors there.

One is on line 410, where:

````
410 IF A(I,J)=0 THEN 440
````

was OCRd/transcribed as:

````
410 IF A(I,J)<>0 THEN 440
````

That inverted its function, so squares were always seen as "occupied".

And then on line 680, the line number for the GOSUB was 810, instead of 910, so the board was never printed.

## Porting

Basic changes were necessary to make `gomoko` run:

The `RANDOMIZE` call was removed as it is neither supported nor necessary.  Also, the calls to `RND` were replaced with `RND(1)` as that is the MS-BASIC equivalent.

The multi-statement separator `\` was replaced with ':'

Some multi-statement lines were split onto multiple lines for clarity (mostly for statements following `GOSUB`s).

Line 5 was added; MS-BASIC seems to support implicit array definition but, apparently, the **implicit** array size is limited to 10x10.  `DIM`ensioning `A` as a 20x20 array prevents board sizes over 10 from erroring-out.
