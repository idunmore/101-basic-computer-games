
# banner.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Various errors here, all well within expectations for OCR with AI-fix-up, but they included variable name substitutions, missing string (`$`) suffixes, transposition of relative/comparison operators (`>` vs. `=`), math operators, and line-number errors (700 vs780) for `GOSUB` targets.

## Porting

This almost feels more like a re-write rather than a "port".

And that feels a bit like cheating; my internal goal was to keep the code "as close to the original as possible".

At the same time, I wanted the code to run and produce (substantially) the same results as the original.

For my sanity, I expanded a fair bit that was on single lines to multiple and that, along with a different output approach (with several special cases), resulted in more than double the number of lines of code vs. the original.

More and more the different `TAB()`  behavior is making things harder to port.  I don't want to make MS-BASIC's `TAB()` modifier work differently to the original ... but I'm not sure it's working correctly (via a serial terminal) relative to the original implementations either ...
