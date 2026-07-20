# bagels.bas

This program required adjustments to the code as part of porting it.

## OCR/Transcription Corrections

**None.**

## Porting

Two significant issues had to be tackled in porting this to MS-BASIC, in addition to minor syntactic changes:

### A BIG Bug
The first is less a "porting" issue, and more that the original code has a bug in it.  That, or the BASIC interpreter it is intended for (RSTS/E running VAX BASIC and PDP-11 BASIC-PLUS-2) has some *very* weird behavior around arrays.

In the original this code is meant to create a 3-digit number with no repeated digits:

````
150 FOR I=1 TO 3
160 A(I)=INT(10*RND)
170 FOR J=1 TO I-1
180 IF A(I)=A(J) THEN 160
190 NEXT J
200 NEXT I
````

But it is written such that it keeps comparing the first generated digit to itself, generating a new digit, and repeating.  Thus it is an infinite loop, and the game "hangs" here.

The following code replaces the above to yield the intended behavior; a three digit number, with each digit stored in an array, with no repeating digits (`PRINT` strings later in the program confirm this is the intended behavior):

````
150 FOR I = 1 TO 3
160 A(I) = INT(10*RND(1))
165 IF I = 1 THEN NEXT I
170 FOR J = 1 TO I - 1
185 IF A(I) = A(J) THEN 160
190 NEXT J
200 NEXT I
````

### Unsupported CHANGE Command

The original version of BASIC that this program was written for (VAX BASIC and PDP-11 BASIC-PLUS-2 running under RSTS/E) supports a BASIC command: `CHANGE`.

`CHANGE` accepts a string of digits and converts it to a supplied array, with the zeroth (0) element of said array being the number of digits in the supplied string, and elements *1* through *n* being the ASC-II values of each subsequent digit.

*See page 136, "CHANGE", in the relevant [BASIC Reference Manual](http://bitsavers.informatik.uni-stuttgart.de/pdf/dec/pdp11/lang/basic/basic-plus-2/AA-L334A-TK_VAX_BASIC_PDP-11_BASIC-PLUS-2_V2_Reference_Manual_198402.pdf).*

To make **bagels.bas** work, I wrote a simple subroutine to perform the same operation, only using the target version of MS-BASIC, and then called it by replacing the original `CHANGE` command on line 250 with a `GOSUB` to my routine on line 1000:

````
1000 REM SIMULATE RSTS/E BASIC PLUS "CHANGE" COMMAND
1010 A1(0) = LEN(A$)
1020 FOR IX = 1 TO LEN(A$)
1030 A1(IX) = ASC(MID$(A$, IX, 1))
1040 NEXT IX
1050 RETURN
````
