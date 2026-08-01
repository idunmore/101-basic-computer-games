# digits.bas

This program required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

There are half a dozen six transcription faults, all of which affect behavior/code legality (primarily in the prediction algorithm).

 `Q=0`  should be `X=0`, `SGN(N)`  should be `SGN(W)`, three weighted terms were incorrectly multiplied instead of added, `M(X,N)`  should be `M(Z,N)`, `NEXT J`  lost its target line number 760, 

The losing-score branch should go to 1010 rather than nonexistent line 1110.

## Porting

- Changed the statement separators from `\` to `:`.

- Replaced `RND` with `RND(1)` to get the syntactically and behaviorally correct output in MS-BASIC.

- Replaced the `MAT` operation with simple initialization loops.

- Added explicit `DIM`ensioning for `N` (in theory, up to 10 elements it can be left implicit).

- Changed the input validation so it doesn't potentially exit an incomplete `FOR/NEXT` (which can cause other issues, later).
