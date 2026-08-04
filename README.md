## 101 BASIC Computer Games

Or perhaps a better title would be:

**"101 BASIC Computer Games for the Ben Eater 6502 running MS-BASIC"**

This is a "project" based on David Ahl's, now-classic, book of type-in games for early versions of BASIC, in which I have completed porting ***ALL*** of them in a **ready-to-run** form for the [Ben Eater 6502](https://eater.net/6502) (and similar) computer, running either [his port of MS-BASIC](https://github.com/beneater/msbasic), or [my own](https://github.com/idunmore/msbasic) (which is based on Ben's), without needing to be able to code yourself.

### About the Source Material
The original source of these programs was as printed listings in a book, David Ahl's "[101 BASIC Computer Games](https://archive.org/details/101basiccomputer0000davi)", the first printing for which was in July 1973; over 50 years ago.

You typed them into your computer yourself, then ran them.  If you transcribed things accurately, they worked; if not, issues could arise - some obvious, some very subtle.

And, since dialects of BASIC had, sometimes significant, differences, you may have had to make adjustments to the code for it to work on your particular computer or version of BASIC.  Occasionally it would be too much to work, or there was no practical workaround, so a feature would have to be changed or dropped.

### Copyright & Public Domain
Per [this](https://blog.adafruit.com/2022/06/16/david-ahl-places-all-his-classic-computing-publications-into-the-public-domain/) news post, David Ahl generously placed all of his written material (books, articles, programs, tutorials) into the Public Domain.

Similarly, any changes or fixes I've made, or new code I've written as workarounds, to the files **within *this* repository** also formally reside in the Public Domain.

## From Book to Files

[Maury Markowitz](https://github.com/maurymarkowitz) undertook scanning, OCRing (with LLM-driven AI assistance), the original programs from the book.  You should definitely read their [notes](https://github.com/maurymarkowitz/101-BASIC-Computer-Games/blob/main/NOTES.md) on the process!  It is not 100% perfect, but the reasons why, and what compensations have been applied, are very interesting.  Some programs have errors as a result (beyond any present in the original code itself).

I consider Maury's work as a wonderful act of preservation.

*Without it, my little undertaking here would **not** be possible.*

## What *I'm* Doing Here (*and now Have DONE, past-tense*)

My purpose is more about nostalgia-driven fun than preservation.

Why build a "retro" computer if not to run "retro" software on it?  Not everyone codes, even those that build such machines.  Once up and running it is both fascinating and entertaining to see what software was created and used at the time; even if it is simple games you typed in from a book.

And, of course, sometimes you just *[want to play those games](https://www.youtube.com/watch?v=GfJJk7i0NTk&t=108s)*.

So, I have done (past tense, now) two things here:

- Taken the source code that Maury has shared and fixed any necessary issues that arose from the OCR conversion, either via reference to scans of the original book or, where that isn't legible/clear, my own fixes.

-  Modified (ported) the "fixed" transcribed code so that it works correctly on the aforementioned versions of MS-BASIC (6502) from 1977 or so (if necessary ... some code will run as-is).

  *Going into this, I was aware of the distinct possibility that not **all** of these programs would necessarily be portable.  If they are too large, or use commands or features that are not supported (and cannot be implemented differently or worked around), then a port may be infeasible.*

Having now completed the "work", I can say that I able to correct and port **100%** of them.

### An Exception ... Sort of ...
Only one program, "`spcwar.bas`", which is a rather nice version of Mike Mayfield's original, and classic, "Star Trek" program, fails the "runs on a standard Ben Eater 6502 build" test.  And that is simply because the code alone simply **doesn't fit** into the available memory of a BE6502 build with 16KB of RAM, and that's without the space the executing code needs for arrays and variables, etc.

I did two things with that ...

- First, I did a full-fat port ... and that works nicely if you've built an otherwise-compatible version of Ben's 6502 but have adapted the memory map to allow 24KB of RAM.

- Second, I trimmed down that version so that it would fit, and run, as-is, on the standard 16KB RAM build ("`spcwar-16k.bas`").  The gameplay is identical; it just omits the comprehensive built-in instructions/manual.  Those elements you can find in the companion markdown file, "`spcwar-16k.md`").

## Understanding this Project & Repository

For each game:

- I first committed an identical copy of the file from [Maury's GitHub repository](https://github.com/maurymarkowitz/101-BASIC-Computer-Games/tree/main).
- I ported the code, making any necessary corrections, and commit that.
- I added an `gamename.md` file describing the nature of the changes required to make the program run on the target versions of MS-BASIC.

  Sometimes this was as simple as "runs as is", "fixed OCR/transcription issues", or more involved if code and logic has to be changed due to differences in the versions of BASIC involved.

This approach makes it easy to compare the original code with the changed code, simply by diffing the two commits.

## Which Games Work?

All of them.

Originally, while this work was "in progress", I stated that:

*"If a game is present in this repository, it can be assumed that it either ran correctly as-is, or has been corrected and any required porting performed, and should be ready-to-run.  At least to the best of my knowledge/testing (which is not exhaustive).*

*See the `gamename.md` file for details on the status of a specific game."*

But now, with all the porting completed, I can say that all of the games run and play.  Indeed, I have run, and played all of the myself on my own BE6502 build.  And I have both won and lost at *least* one game in every case, as part of trying to ensure my "porting efforts" weren't missing something.

### Bugs

There **will** be some.

There certainly are in the original listings!

Per above, I have played all of these games, to completion, as both winner and loser.  And that was both enjoyable and fascinating.  But there's no chance that there aren't lurking bugs; be they a result of my porting efforts, or logic issues in the original code that I have then ported faithfully!


### What Was Needed (on a Per-Program Basis):

Various types of work were required in correcting and porting these programs, and the commit messages indicate this as follows:

| Message                  | Meaning                                                                 |
|--------------------------|-------------------------------------------------------------------------|
| Add original source file | The original source code runs **as-is**; `gamename.md` will be  present |
| Ported                   | Code changes were required to run under MS-BASIC                        |
| Corrected                | Fixes to the OCR/transcription were required                            |
| Corrected and Ported     | Fixes to the OCR/transcription and code changes were required           |

Each program includes a like-named `.md` file that details what was done both from an OCR/transcription perspective and from a true "porting" perspective (i.e., accounting for the differences in BASIC dialects and system capabilities).

### Running these Games

The easiest way to run these games is to copy-and-paste the code directly from the GitHub file view into the Serial Terminal interface connected to your "BE6502", while it is running MS-BASIC.  If you've not gone as far as implementing flow-control, and input buffering, in Ben's videos, you'll need to set your "character pacing" in your terminal program to a value that prevents the data coming into the computer too fast.

You could, of course, **type** the code in yourself, but that might be a bit *too* much of a nostalgia trip even for me.

### Learnings

I've added a "[LEARNINGS.md](https://github.com/idunmore/101-basic-computer-games/blob/main/LEARNINGS.md)" file to track new things I've learned about MS-BASIC (in lieu of a specific manual) during the course of porting/converting these games.

### Copy vs. Fork
Why a copy, not a fork?

- A fork would bring over all the original files.  I only want to include files that I have successfully ported or fixed.  There's no reason to have them in this repository otherwise.   It would just add confusion, since the intent is that these are ready-to-run for a specific set up.

- I don't intend to submit PRs upstream, since that would defeat the point of the original.

- And finally, since there's a good chance some games cannot be ported, I may cheekily rename the repository/project to "Not *Quite* 101 BASIC Computer Games" or "Very Nearly 101 BASIC Computer Games" ... or the first name I mentioned in the intro.

## AI Usage (or lack thereof)

Entirely minimal.

The joy, for me, in retro-computing and programming is about nostalgia.  Porting these programs was, while at times frustrating (as all programming efforts can be), very fulfilling.  It was a transport back-in-time.  It was an experience.  And carried some most enjoyable "learnings" (learning is my very favorite thing to do).

*Turning it over to AI would have robbed me of that.*

Thus, while it was not an explicitly stated "goal" to avoid using AI here, if that had been the "plan" *I'd* just as soon not have bothered, so there is very little of it.

At the same time, I'm not a masochist.

AI was used in correcting the OCR/transcriptions and porting code for, I think, just **five** of these programs.  The companion "`.md`" files call out where this was done *everywhere* it was done.  And in every case, I'd done substantial work on the corrections and porting myself already.  I pretty much only invoked AI (OpenAI Codex in this case, on Sol 5.6) when I'd already spent more time than made any sense on a specific problem and wasn't making any progress.

Also, there were a few cases (again, all explicitly called out in the companion "`.md`" files) where I got so engrossed in trying to fix a gnarly/subtle issue that I forgot to make notes on what I was actually correcting or fixing.  So, to complete the details for the "`.md`" files, I had AI analyze and narrate the diffs to create those sections.

## The "Bunny Bonus"

The original book omits a listing for "`bunny.bas`".

As a "celebration" (and a bit of fun), I decided to remedy that; details are in the "`bunny.md`" file.
