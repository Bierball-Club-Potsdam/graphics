# graphics

## repo overview

The `domain`/`fullName`/`fullNameDomain`/`minimal` directories contain SVGs with the respective logo variant. Each is stored as `logo.svg`, containing editable text, and `logo_textAsPath.svg`, which has the text converted to paths to avoid font issues.

The `print` directory contains print-ready PDFs with correct CMYK colors.

## display colors (RGB)

- Yellow: #fce190
- Blue: #0e2b68
- Green: #30983e

## print colors (CMYK)

- Yellow: 0.03922 0.10588 0.52157 0.00392
- Blue: 0.92941 0.83137 0.06275 0.33333
- Green: 0.77255 0.05882 0.90196 0.18039

## creating a print-ready pdf

Problem: Neither SVG nor Inkscape properly support CMYK.  
Solution: Create finished SVG in Inkscape first, then assign correct colors using Scribus.

- choose the desired logo variant
  - if possible, use the `_textAsPath` variant
  - if not available, convert the text to paths in Inkscape by selecting it and choosing `Path > Object to path`
- if the print service provides a template, use it to correctly set up the page
  - hint: the objects panel is helpful for selecting obstructed elements (`Object > Objects`)
  - group all logo elements to avoid errors  (`Object > Group` or `ctrl + g`)
  - import the template (`File > Import` or `ctrl + i`)
  - lower it to bottom  (`Object > Lower to bottom` or `end`)
  - resize the page to fit the template
    - select template
    - `File > Document properties > Resize page to content`
    - ensure margins are set to zero
    - `Resize page to drawing or selection`
  - place the logo according to the template
  - remove the template
  - recommended: add a rectangle filling the whole background with the same color as the outer parts of the logo just to make sure
- export the logo as plain SVG for better compatibility:
  - `File > Save a copy`
  - Select `Plain SVG` as file type
- open the plain SVG in Scribus
  - Scribus might still complain about unsupported features - just make sure the logo looks right
- replace the colors using `Edit > Colors`
  - the RGB colors are marked by R/G/B stripes icon instead of C/M/Y/K squares icon
  - open RGB color, change color model to CMYK, make sure values are close to values stated above
- export as PDF
  - during export, go to the `Color` tab and switch the output mode to `Printer` to enable CMYK export
