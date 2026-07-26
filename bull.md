# bull.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Changes here were mostly minor OCR issues, some missing parenthesis resulting in illegal syntax and a few  `GOTO`  line numbers getting muddled.

## Porting

Porting was interesting:

That began with usual removal of `RANDOMIZE`  and switching `RND(0)` calls to `RND(1)`.

Function definition was moved ahead of where it is called.

The biggest change was a result of the function definition on line 1390:

````
1390 DEF FNC(Q)=(4.5+L/6-(D(1)+D(2))*2.5+4*D(4)+2*D(5)-(D(3)^2)/120-A)*RND(0)
````

This length of this line exceeds *this* MS-BASIC's maximum of 72 characters.

To remedy this I created a subroutine that splits the operation over several lines, and then modified the calling code to use it:

````
2100 REM SUBSTITUTE FN AS LINE IS TOO LONG AS-IS
2110 Q=4.5+L/6-(D(1)+D(2))*2.5+4*D(4)+2*D(5)
2120 Q=Q-(D(3)^2)/120-A
2130 Q=Q*RND(1)
2140 RETURN
````

The calling code changes from:

````
1460 IF FNC(Q)<2.4 THEN 1570
````

to:

````
1455 GOSUB 2100
1460 IF Q<2.4 THEN 1570
````
