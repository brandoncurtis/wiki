---
title: LaTeX Typesetting
permalink: /LaTeX_Typesetting/
---

Installing LaTeX in Ubuntu 14.04 Trusty Tahr
--------------------------------------------

Just run this from the command prompt:

`sudo` `apt-get` `install` `texmaker` `biber`

Launch TexMaker and configure it as follows:

-   Bib front-end: biblatex
-   Bib back-end: biber
-   bib(la)tex config: "biber %"
-   Quick-Build config: "latex, bib(la)tex, latex (x2), view pdf"

This should work fine, without problems!

Usage Details
-------------

### Bibtex vs Biber

Special characters will fail if you use the obsolete bibtex backend, as it is pretty much ASCII-only (any UTF-8 in the \*.bib makes it explode).

Biber hasn't been packaged for Precise, so you'll need to compile from source, retrieve through \[tug.org\], or find a [backport](http://tuxette.nathalievilla.org/?p=1368) ([sourceforge](http://sourceforge.net/projects/biblatex-biber/files/biblatex-biber/)) if you're using 12.04.

On 12.04, apt-cache show biblatex yields: Config-Version: 1.7-1 Recommends: biber (&gt;= 0.9.6)

Ubuntu 12.04 uses biblatex version 1.7-1; you can verify this by running:

`apt-cache` `show` `biblatex`

According to the biber documentation, the last biber release to support biblatex 1.7 is biber 0.9.9:

-   [Biber/BibLaTeX compatability matrix](http://i.stack.imgur.com/4O4Gx.png)
-   [Biber documentation](http://sourceforge.net/projects/biblatex-biber/files/biblatex-biber/1.0/documentation/biber.pdf/download)

...so this should do it: <http://sourceforge.net/projects/biblatex-biber/files/biblatex-biber/0.9.9/binaries/Linux/>

-   [Bibtex vs Biber and Biblatex vs Natbib](http://tex.stackexchange.com/questions/25701/bibtex-vs-biber-and-biblatex-vs-natbib)
-   [StackExchange - Compatibility between Bibtex and BibLaTeX bibliography files](http://tex.stackexchange.com/questions/37095/compatibility-of-bibtex-and-biblatex-bibliography-files)
-   [StackExchange - Bibtex vs BibLaTeX](http://tex.stackexchange.com/questions/8411/what-is-the-difference-between-bibtex-and-biblatex)
-   [StackExchange - Switching to BibLaTeX](http://tex.stackexchange.com/questions/5091/what-to-do-to-switch-to-biblatex)
-   [Sourceforge - BibLaTeX Biber](http://biblatex-biber.sourceforge.net/)
-   [Wikipedia - Biber (LaTeX)](http://en.wikipedia.org/wiki/Biber_(LaTeX))

== References

-   <https://www.sharelatex.com/learn/>
-   <http://tex.stackexchange.com/>
-   <http://www.tug.dk/FontCatalogue/>
-   <http://www.tex.ac.uk/>
-   <https://www.latex-tutorial.com/>

<!-- -->

-   <https://en.wikibooks.org/wiki/LaTeX/>
-   <http://www.dickimaw-books.com/latex/>

Blogs that discuss LaTeX

-   <http://texblog.org/>
-   <http://timmurphy.org/category/latex/>

[Category:Software](/Category:Software "wikilink")