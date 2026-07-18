## Learnings

I can find no specific "manual" or "reference" to the version of MS-BASIC this project targets.  While many BASIC constructs are common across dialects, features, keywords and syntax can vary.

This file captures specific things I've learned about the [target version of MS-BASIC](https://github.com/idunmore/msbasic) as I work through porting the original "101 BASIC Computer Games" to it.

### Support for Multi-Statement Lines

You can chain statements on a single line by separating them with a colon, "`:`".

*Some other BASIC dialects use "`\`" as the statement separator; in most cases a colon can be directly substituted.*
