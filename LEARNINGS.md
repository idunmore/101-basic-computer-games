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