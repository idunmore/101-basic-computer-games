# hang.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Changes here were mostly minor OCR issues, transposing `1`  for `I` and vice-versa, and one or two misses on line numbers for `GOTO` targets.

## Porting

Porting was fairly involved:

The usual removal of `RANDOMIZE` was the sole, obvious, change.

### FOR/TO as Statement Modifier
DEC BASIC supports the use of `FOR/TO` as a statement *modifier*, which is not something I'd seen in other BASIC dialects (and is definitely **not** supported in MS-BASIC):

The code:

````
100 A$(I)="X" FOR I=1 TO 10
````

is a) legal in DEC BASIC (at least for BASIC 2 PLUS) and b) is equivalent to this:

````
100 FOR I=1 TO 10: A$(I)="X": NEXT I
````

Once I'd figured this out, there were about a dozen places that had to be adjusted.

### ELSE clauses

MS-BASIC doesn't support these, and depending on how they are used in the original code, it is necessary to simulate them by inverting expressions and then jumping over the `true` case.

This happened in some compound statements enough that it was a bit fiddly to unwind.

### BUGs

It's possible these were a result of my initial changes to address the `ELSE` issues, but even without those when I look at the code I cannot see how the original logic could function *correctly* - at least not with how I understand BASIC to function, nor based on reading the relevant sections of the DEC BASIC reference.

In short, the routine that matches letters to see if they're in the hidden word would ONLY find the first occurrence of a letter.  And then that letter goes into the "already guessed" letters, so you can't guess it a second time.  This made it impossible to organically solve any word that had a repeated character!

In the end, I effectively re-wrote part of this logic (lines 210 through 310, with the main changes between 250 and 270).

It now works as the illustrated play through suggests.
