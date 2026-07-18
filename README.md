## 101 BASIC Computer Games

Or perhaps a better title would be:

"*Hopefully* 101 BASIC Computer Games for the Ben Eater 6502 running MS-BASIC"

This is a "project" based on David Ahl's, now-classic, book of type-in games for early versions of BASIC, intended to have them ready-to-run on the [Ben Eater 6502](https://eater.net/6502) (and similar) computer, running either [his port of MS-BASIC](https://github.com/beneater/msbasic), or [my own](https://github.com/idunmore/msbasic) (which is based on Ben's), without needing to be able to code yourself.

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

## What *I'm* Doing Here

My purpose is more about nostalgia-driven fun than preservation.

Why build a "retro" computer if not to run "retro" software on it?  Not everyone codes, even those that build such machines.  Once up and running it is both fascinating and entertaining to see what software was created and used at the time; even if it is simple games you typed in from a book.

And, of course, sometimes you just *[want to play those games](https://www.youtube.com/watch?v=GfJJk7i0NTk&t=108s)*.

So, I am doing two things here:

- Taking the source code that Maury has shared and fixing any necessary issues that arose from the OCR conversion, either via reference to scans of the original book or, where that isn't legible/clear, my own fixes.

- Where possible, modifying (porting) the code so that it works correctly on the aforementioned versions of MS-BASIC (6502) from 1977 or so (if necessary ... some code will run as-is).

  *Not *all* programs will necessarily be portable.  If they are too large, or use commands or features that are not supported (and cannot be implemented differently or worked around), then a port may be infeasible.*

## Understanding this Project & Repository

For each game:

- I am first committing an identical copy of the file from [Maury's GitHub repository](https://github.com/maurymarkowitz/101-BASIC-Computer-Games/tree/main).
- I port the code, making any necessary corrections, and commit that.
- I add an `gamename.md` file describing the nature of the changes required to make the program run on the target versions of MS-BASIC.

  This may be as simple as "runs as is", "fixed OCR/transcription issues", or more involved if code and logic has to be changed due to differences in the versions of BASIC involved.

This approach makes it easy to compare the original code with the changed code, simply by diffing the two commits.

### Which Games Work?

If a game is present in this repository, it can be assumed that it either ran correctly as-is, or has been corrected and any required porting performs, and should be ready-to-run.  At least to the best of my knowledge/testing (which is not exhaustive).

### Copy vs. Fork
Why a copy, not a fork?

- A fork would bring over all the original files.  I only want to include files that I have successfully ported or fixed.  There's no reason to have them in this repository otherwise.   It would just add confusion, since the intent is that these are ready-to-run for a specific set up.

- I don't intend to submit PRs upstream, since that would defeat the point of the original.

- And finally, since there's a good chance some games cannot be ported, I may cheekily rename the repository/project to "Not *Quite* 101 BASIC Computer Games" or "Very Nearly 101 BASIC Computer Games" ... or the first name I mentioned in the intro.
