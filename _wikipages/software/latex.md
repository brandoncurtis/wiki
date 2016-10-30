---
layout: default
title: LaTeX Document Typesetting
permalink: p/latex
category: software
---

## Markdown to TeX to HTML (with PNG equations)

+ https://www.tug.org/tex4ht/
+ https://github.com/michal-h21/helpers4ht/wiki/tex4ht-tutorial
+

"TeX4ht is a system for converting documents written in TeX/LaTeX/ConTeXt/etc. to HTML, various XML flavors, braille, etc., optionally using MathML."

+ https://www.tug.org/applications/tex4ht/mn.html

TEX4ht: HTML Production

+ https://www.tug.org/TUGboat/tb25-1/gurari.pdf
+ http://access2science.com/latex/tutorial_txht.xhtml#x1-90003

"This document intends to give you a quick introduction to tex4ht, providing instructions on getting it installed and some very basic usage."

`sudo apt install tex4ht`

LaTeX/Export To Other Formats

+ https://en.wikibooks.org/wiki/LaTeX/Export_To_Other_Formats

this converts latex formula-by-formula into images:

+ http://www.nought.de/tex2im.php
+ http://www.makeuseof.com/tag/tex2img-convert-latex-equations/
+ https://www.fourmilab.ch/webtools/textogif/textogif.html
+ https://tex.stackexchange.com/questions/34054/tex-to-image-over-command-line/34058#34

[Passing arguments to htlatex](https://groups.google.com/forum/#!topic/comp.text.tex/eQFyCQflD4U)

    Doesn't tex4ht and t4ht run in batch mode only? Perhaps you mean the
    preceding latex runs. For example htlatex wrapper runs latex 3x and
    then tex4ht followed by t4ht. You can pass additional options to latex
    run as 5th parameter to htlatex, e.g.:

    htlatex filename "" "" "" "-interaction=batchmode"

    http://www.cse.ohio-state.edu/~gurari/TeX4ht/mn-commands.html


## `latexmk`

+ http://paulklemm.com/blog/2016-03-06-watch-latex-documents-using-latexmk/
+ http://jon.smajda.com/2008/03/08/latexmk/


## Additional Packages

Many people are recommending the `beamer` package.  Look into this!


## Development Ideas

write a Markdown parser that pulls out embedded LaTeX, converts to png with latex2img, renders the Markdown to HTML, and reinserts the images into the html!
