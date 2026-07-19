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
