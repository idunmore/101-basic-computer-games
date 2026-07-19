# rusrou.bas

This file required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.


## OCR/Transcription Corrections

Line 40 was missing a period (which is **not** visible in the scan of the original page).  Interpreted without that period, the syntax would be illegal, and the actual OCR/transcription resulted in:

````
40 IF RND(0)>83333 THEN 70
````

That is syntactically legal, but the `IF` condition would never be met (`RND(0)` generates a fractional number).

What the code is doing is using a random number with a range of 0 to 0.99999 (or so, but effectively 0 to 1) to represent an outcome with a 1 in 6 chance of occurrence.

So:  `1 / 6 = 0.16666`
*then:* `1 - 0.16666 = 0.83333`
**thus:**  A result of `> 0.83333` is a 1 in 6 chance - (assuming a truly random distribution from `RND(1)` ... which of course is not the case).

Given the likelihood the missing period is missing because it is small, and replacing it yields exactly the value that would make sense given the above, we can be very confident that the original line of code is actually:

````
40 IF RND(0)>0.83333 THEN 70
````

Which then just needs to be changed to:

````
40 IF RND(1)>0.83333 THEN 70
````

to work with the target version of MS-BASIC.

## Porting

The unsupported command `RANDOMIZE` was removed (line 5), and the  `RND(0)` call in line 40 was changed to `RND(1)`, since `RND(0)` will always generate the same number for a given run in the target version of MS-BASIC.
