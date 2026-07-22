
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
