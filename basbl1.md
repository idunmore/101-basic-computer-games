# basbl1.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

I also took a major liberty with the code, since it is not readily possible to recreate the full "experience" of the original without modifying MS-BASIC, and your hardware, to allow for loading/chaining files.

*That liberty was to combine [basbal.bas](https://github.com/idunmore/101-basic-computer-games/blob/main/basbal.bas)  and this file, `basbl1.bas`, into a single program.*

As long as your build of the "BE6502" has >=16KB of RAM, and you didn't specify a different memory size when running MS-BASIC, this all fits in memory at once.  And this helps with the intent, here, that you should just be able to "load and run" these conversions.

## OCR/Transcription Corrections

Most of these were the usually array of symbol interpretation issues (possibly exacerbated by an AI pass "correcting" for what "seems logical".  This includes things like getting equality tests when the listing has greater-than, and incorrectly getting `<>` from `<`.

Also, an occasional "stray" character, typically at line-ends, due to "noise" in the print/scan (I assume), were corrected.

## Porting

I first started poking away at this a week(ish) ago.  It was slow going, despite being only 140 lines or so.

Some of it was simple; switching statement separators, proper `RND()` syntax/values, and so on.

But then, the code is dense, most of it having multi-statement lines.  It employs conditionals using implicit `ELSE` behavior (which MS-BASIC doesn't directly support).  The decision to combine the "loader" and the "game" required extensive, manual, renumbering, and so on.

The changes are extensive, if not *logically* complicated (though not having named procedures or UDFs makes for an uncomfortable "mental working set"), and the result is the full SLoC count jumping from a combined ~180 lines to over 330.  Keeping track of them all was something I just stopped caring about.

After correcting/porting 67 of these programs **100% manually** (which is the fun, and educational, part for me), I had had enough of this one.  It takes a while to play through to check behavior, issues don't show up every game, which didn't help.

So, with, I'd say, about 85% of the work done, I decided to see what **AI** could do with it (specifically OpenAI Codex, Sol 5.6 on high-effort).  That churned for a solid 15 minutes, but seems to have "finished the job" rather well (to the degree I can tell).  Mostly it found some issues (bugs, really), that I'd either missed in the original or inadvertently introduced in my porting, but it did finish the work.

For me, working on retro-systems/code is a nostalgia-trip, so 100% of the fun is in "doing it myself".  Thus *this* one is a **lot** less satisfying, despite the effort, than any of the others to date.  It would be relatively trivial to build a couple of simple skills to let AI do the rest of the conversions

*I won't.*

It defeats the point, for **me**.

*But* if/when I use any AI assistance on other conversions, it will be **explicitly** called out (having looked at ALL the listings, as I pick-and-choose which to convert next, I suspect "yahtze" may involved some AI-assist ... if only for the sake of what is left of my sanity).
