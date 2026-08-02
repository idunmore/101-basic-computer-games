# tictac.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

The `DATA` statement on line 2150 was missing a value (a `0` in the series of `0`s), which caused an "out of data" error.

## Porting

The following code, that generates a random move for the computer, can get into a situation in which `M` or `N` have values that cause the `RND()` calls to keep generating the same number over and over (a value of zero would do this).

If that happens, and the generated number is either `0` (very unlikely) or `>3` (entirely possible, since the range is really `0` to `0.999999 * 3.33` here), the result is an infinite loop.

````
1090 REM PROGRAM TO MAKE MOVE FOR THE MACHINE....
1100 LET M=INT(3.33*RND(M))
1110 LET N=INT(3.33333*RND(N))
1120 IF M=0 THEN 1100
1130 IF M>3 THEN 1100
1140 IF N=0 THEN 1110
1150 IF N>3 THEN 1110
````

So the `RND(M)` and `RND(N)` calls were replaced with `RND(1)` which will generated different numbers on each call.

Finally, I `REM`oved the `CHAIN "DEMON"` statement as a) `CHAIN` isn't supported here and b) the "DEMON" program doesn't exist here either.
