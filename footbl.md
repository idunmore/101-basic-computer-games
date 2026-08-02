# footbl.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

There were quite a few of these, some of which took a while to find since they didn't all cause outright errors.

You can look at the diff to see all of the changes, but some of the highlights include:

The yardage calculation (line 3080) was corrupted, and had to be manually restored to: `G=D(A,M1)+FNT(Q)*(D(2,M1)-D(A,M1))/3.5`

Multiple transpositions of `+` for `*`, including lines 650, 1290 and 1560.

Some semicolons in print statements were restored, so that output formats/reads correctly.

The timeout counter was increasing instead of decreasing (line 2690, `U2+1` instead of `U2-1`.

And other similar types of changes; most *materially* affected gameplay.

## Porting

Very little was required here, just removing the `RANDOMIZE` call (line 420) since it is not supported in our MS-BASIC, and replacing `RND(X)` with `RND(1)`.

`RND(X)` would likely still work here, as `X` appears to always have a value of `>=1`, but it wouldn't produce a different result, so using what I know works.
