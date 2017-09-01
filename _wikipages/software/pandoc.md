---
title: Pandoc Text Converter
permalink: p/pandoc
layout: wikipage
category: software
math: true
---

* toc
{:toc}

----

### Overview

[Pandoc](http://pandoc.org/) is a command line tool for interconverting between markup languages.  Pandoc supports common languages like HTML, Markdown, and LaTeX, common document formats like docx and epub, and lots of weird stuff I've never heard of before.

$$
R_{\mu \nu} - {1 \over 2}g_{\mu \nu}\,R + g_{\mu \nu} \Lambda
= {8 \pi G \over c^4} T_{\mu \nu}
$$

For example, Pandoc can convert Markdown with inline $\LaTeX$ into a PDF:

    pandoc pandoc.md -f markdown -t latex -s -o pandoc.pdf

You can generate an intermediate .tex file, customize it, then [convert it to a PDF]({{ site.baseurl }}/files/pandoc.pdf) in a separate step:

    pandoc pandoc.md -f markdown -t latex -s -o pandoc.tex
    pdflatex pandoc.tex

To roll right through errors and clean up the $\LaTeX$ build files after generating the PDF, I created this script:

    #!/bin/bash
    mymd="$1"
    mytex="$(echo "$mymd" | sed s/.md/.tex/)"
    pandoc "$mymd" -s -f markdown -t latex -o "$mytex"
    latexmk -pdf -f -interaction=nonstopmode "$mytex"
    latexmk -pdf -f -c
