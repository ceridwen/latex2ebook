## Synopsis

This project provides tools for displaying the output of LaTeX files
on ebook readers, in particular Kindles.

## Code Example

There are two possible conversion paths, to PDF and to Kindle's native
ebook format.  The PDF conversion is much simpler but doesn't have
some of the advantages of ebooks like reflowable text.

### PDF

Add pdf-ebook.sty to the LaTeX file's directoy and add
`\usepackage{pdf-ebook}` to the preamble, then compile as normal with
pdflatex or lualatex.  Depending on the size of the ebook reader, it
may be necessary to edit pdf-ebook.sty to set geometry correctly.

### Kindle

This requires TeX4ht (https://www.tug.org/tex4ht/), dvisvgm (http://dvisvgm.sourceforge.net/), and Kindlegen (http://www.amazon.com/gp/feature.html?docId=1000765211) or Calibre (http://calibre-ebook.com).

Add images.cfg to the directory and run,

````
htlatex <name>.tex images.cfg "-c dvisvgm" "-interaction=nonstopmode"
````

and (with Calibre)

````
ebook-convert <filename>.html .azw3 --pretty-print
````

or (with Kindlegen)

````
kindlegen <filename>.html
````

fonts-ebook.sty is an experimental package that selects fonts that
display better on ereaders, for both conversion paths.

## Motivation

Standard LaTeX files don't display well on ebook readers.

## Installation

pdf-ebook.sty uses the geometry and ifpdf packages, both of which are
distributed with TeX Live.
