# synonm.bas

This program required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

Porting this yielded some new learning:

It began with usual removal of `RANDOMIZE`  and switching `RND` calls to `RND(1)` .

Next, some of the `DATA` statements exceeded the maximum line-length for our target version of MS-BASIC (72 characters).  For these, I removed the last "word" on each line, and reduced the word count in the first value of that line's `DATA` statement to match.

Then I modified the use of `FOR-TO` as a *statement modifier* on line 232, and expressed it as an MS-BASIC-compatible loop.

The "**new learning**" was triggered by line 230 throwing a "NEXT without FOR" error once a correct guess had been made.

All of the versions of BASIC I used as a child/teenager were **explicit** about not prematurely exiting `FOR/NEXT` loops (i.e., not `GOTO`ing out of them), and the fact it would corrupt the stack.

MS-BASIC is **firmly** in this camp.

It seems that RSTS/E BASIC-PLUS, in common with modern BASIC dialects, performs appropriate stack clean-up when prematurely exiting a `FOR/NEXT` loop. 

This means the code works correctly on its original target system, but on simpler BASIC implementations, corrupts the stack and results in the aforementioned error.

To fix this, I changed lines 260 through 290:

````
260 FOR J=1 TO N2
270 IF G=J THEN 290
280 IF A$=W$(J) THEN 320
290 NEXT J
````

to:

````
260 K=0:FOR J=1 TO N2
270 IF G=J THEN 290
280 IF A$=W$(J) THEN K=1
290 NEXT J
295 IF K THEN 320
````

So that the `J` loop could **complete**, and still then jump to where it needs to, and avoid leaving the `J` loop counter on the stack, where the `NEXT I` on line 230 would then be "confused" and throw an error.
