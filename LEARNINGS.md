
## Learnings

I can find no specific "manual" or "reference" to the version of MS-BASIC this project targets.  While many BASIC constructs are common across dialects, features, keywords and syntax can vary.

This file captures specific things I've learned about the [target version of MS-BASIC](https://github.com/idunmore/msbasic) (as opposed to BASIC in general) as I work through porting the original "101 BASIC Computer Games" to it.

### Support for Multi-Statement Lines

You can chain statements on a single line by separating them with a colon, "`:`".

*Some other BASIC dialects use "`\`" as the statement separator; in most cases a colon can be directly substituted.*

### Assumed GOTO in IF/THEN Statements

Instead of:

````
IF A = 0 THEN GOTO 100
````

The `GOTO` can be omitted, with the same meaning:

````
IF A = 0 THEN 100
````

### ON GOTO Support

The `ON GOTO` statement allows for powerful conditional branching.  The `ON` clause accepts a 1-based variable that determines which of multiple, comma-separated, line numbers the `GOTO` passes control:

````
10 A = 1
20 ON A GOTO 40, 60, 80
30 END
40 PRINT "A = 1 COMES HERE"
50 END
60 PRINT "A = 2 COMES HERE"
70 END
80 PRINT "A = 3 COMES HERE"

````

### ON GOSUB Support

The `ON GOSUB` statement allows for powerful conditional branching.  The `ON` clause accepts a 1-based variable that determines which of multiple, comma-separated, line numbers the `GOSUB` passes control:

````
10 FOR A = 1 TO 3
20 ON A GOSUB 50, 70, 90
30 NEXT A
40 END
50 PRINT "A = 1 COMES HERE"
60 RETURN
70 PRINT "A = 2 COMES HERE"
80 RETURN
90 PRINT "A = 3 COMES HERE"
100 RETURN

````

### Implicit Array DIMensioning (and ReDIMensioning)

Referencing a variable with subscripts, such as A(1,1), before it has been `DIM`ensioned appears to implicitly create an array.  It can be subsequently resized, also, by assigning to higher subscript values.

This seems to make the **explicit** use of `DIM` *mostly* unnecessary.

Implicitly dimensioned arrays (i.e., arrays referenced as such without being explicitly `DIM`ensioned **are limited to 10 elements per dimension** (so you can reference A(10,10) without `DIM`ensioning `A`, but `A(11,10)` would yield an error.

Also, executing a `DIM` statement against an *implicity* created array results in a ReDIMensioning error.

### FOR-NEXT Always Executes at Least Once

FOR-NEXT loops in MS-BASIC **always** execute **at least once**, even if the `TO` criteria have been satisfied before the **first** loop iteration:

````
10 FOR A = 1 TO 1
20 PRINT A
30 NEXT A
````

Will print:

`1`

Most of the BASIC dialects I've tested this with behave the same way, although some (such as RSTS/E running VAX BASIC and PDP-11 BASIC-PLUS-2) either don't, or have variations of `FOR-NEXT` that make the run-at-least-once behavior conditional.

This in contrast to languages like `C` where the `for` look only runs if the exit criteria are **not** met.

### PRINT can be abbreviated as ? (on entry ONLY)

MS-BASIC will let you enter `?` instead of the word `PRINT` when entering code.  However, it will expand it to the word `PRINT` when you hit enter on that line of code.

If you type:

````
10 ? "Hello, world!"
````

and then `LIST` the program, you'll get:

````
10 PRINT "Hello, world!"
````

## Non-MS-BASIC Learnings Useful in Porting TO MS-BASIC

While porting a number of these programs I've not only solified my understanding of what is, and isn't, supported by MS-BASIC, but also learned a fair bit about interesting behaviors, keywords, commands and so on for the BASIC dialects that the *original* programs are written for.

These dialects include Dartmouth BASIC and DEC VAX/VMS, RSX-11M-PLUS, RSX11M, and RSTS/E running VAX BASIC and PDP-11 BASIC-PLUS-2 ... among others.

### FOR-TO As a STATEMENT Modifier

In DEC BASIC you can use `FOR-TO` statements to modifier another statement:

````
10 A$(I) = "X" FOR I = 1 TO 10
````

has the same effect as:

````
10 FOR I = 1 TO 10: A$(I) = "X": NEXT I
````

Note that the `NEXT` is not required (nor supported) in the first, statement-modifying, case.

### Early FOR/NEXT Exit - "Control Stack" Clean-Up

Industrial versions of BASIC, such as BASIC-PLUS, support automatically cleaning up their "control stack" when code branches out of a `FOR/NEXT` loop without meeting to `TO` condition.

Most "home computer" dialects of BASIC, including the original 6502 versions of MS-BASIC, do not handle this, and exitinga `FOR/NEXT` loop early, by `GOTO`ing out of it, will result in the "control stack" becoming "corrupt", and will yield *"NEXT without FOR"* errors the next time a `NEXT` statement is processed.

