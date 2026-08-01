# rocket.bas

This program required **both** corrections from the OCR/transcriptions, and adjustments to the code as part of porting it.

## OCR/Transcription Corrections

Several, with significant impacts on behavior:

- Restored `A=I:V=J` vs. the transcribed  `A=I=V=J`

- Corrected `G-Z/K/M` to `G-Z*K/M`.

- Rebuilt the corrupted velocity/thrust equations:

    - `W=(1-M*G/(Z*K))/2`
    - `S=M*V/(Z*K*(W+SQR(W*W+V/Z)))+.05`

- Fixed "powers" for the velocity series - `Q^2/2`, `Q^3/3`, `Q^4/4`, and `Q^5/5`

- Fixed the altitude series:

  -  `G*S^2/2`
  - `Q/2+Q^2/6+Q^3/12+Q^4/20+Q^5/30`

- Corrected the depth calculation for cratering, changing `W*2777` to `W*.277`

## Porting

- Replaced `\` statement separators with `:`

- Split various lines into multiple to stay within the MS-BASIC line-length limit (72 characters)

- Adjusted semicolon use in `PRINT` statements to get the correct layout.

- Moved various update routines into subroutines or refactored inline code, and adjusted structure so they update on each "10 second" interval (my first set of changes kept asking for the 0-second burn data).
