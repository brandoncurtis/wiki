---
title: MediaWiki Setup Math Rendering
permalink: "/MediaWiki_Setup_Math_Rendering/"
---

Installing Prerequisites
------------------------

[MediaWiki—Manual: Math](http://www.mediawiki.org/wiki/Manual:Math) [MediaWiki—Manual: Enable Tex](http://www.mediawiki.org/wiki/Manual:Enable_TeX)

To work properly with rendering non-ASCII Unicode characters, a supplemental TeX package is needed (cjk-latex in Debian)

In Ubuntu Precise, all dependencies can be installed using:

`sudo` `apt-get` `install` `build-essential` `dvipng` `ocaml` `texlive-fonts-recommended` `texlive-lang-greek` `texlive-latex-recommended`

Installing the Extension
------------------------

<http://www.mediawiki.org/wiki/Extension:Math>

Install it in the Extensions folder: git clone <https://gerrit.wikimedia.org/r/p/mediawiki/extensions/Math.git>

    require_once "$IP/extensions/Math/Math.php";
    // Be sure to have a math directory with writing
    // permission and that these two variables are set or
    // default to that directory:
    $wgMathDirectory = 'filesystem/path/of/the/math/directory';
    $wgMathPath = 'URL/path/of/the/math/directory';

info: <nomathjax><http://www.mediawiki.org/wiki/Manual:$wgMathPath></nomathjax> <nomathjax><http://www.mediawiki.org/wiki/Manual:$wgMathDirectory></nomathjax>

run update.php

info: <http://www.mediawiki.org/wiki/Manual:Update.php>

Compiling the Pieces
--------------------

compile texvc

via: <http://www.mediawiki.org/wiki/Manual:Enable_TeX>

"texvc takes LaTeX-compatible equations and produces formatted output in HTML, MathML, and (via LaTeX/dvipng) rasterized PNG images. Input data is parsed and scrutinized for safety, and the output includes an estimate of whether the code is simple enough that HTML rendering will look acceptable."

    brandon@patientzero:/etc/mediawiki/wiki-plasmed/extensions/Math/math$ make

to use texvccheck: <http://www.mediawiki.org/wiki/Texvccheck>

    brandon@patientzero:/etc/mediawiki/wiki-plasmed/extensions/Math/texvccheck$ make

Testing
-------

If it worked, this block of code:

     <math>
      \operatorname{erfc}(x) =
      \frac{2}{\sqrt{\pi}} \int_x^{\infty} e^{-t^2}\,dt =
      \frac{e^{-x^2}}{x\sqrt{\pi}}\sum_{n=0}^\infty (-1)^n \frac{(2n)!}{n!(2x)^{2n}}
     </math>

Should yield this:

\(\operatorname{erfc}(x) =
  \frac{2}{\sqrt{\pi}} \int_x^{\infty} e^{-t^2}\,dt =
  \frac{e^{-x^2}}{x\sqrt{\pi}}\sum_{n=0}^\infty (-1)^n \frac{(2n)!}{n!(2x)^{2n}}\)

via the Math extension README: If some equations render correctly while others don't, you probably don't have AMS\* packages for LaTeX installed. Most distributions of TeX come with AMS\*. In Debian/Ubuntu AMS\* is in tetex-extra package. To check if that is the problem you can try those two equations:

`   x + y`
`   x \implies y`

The first uses only standard LaTeX, while the second uses symbol \\implies from AMS\*. If the first renders, but the second doesn't, you need to install AMS\*.

\(x + y\)

\(x \implies y\)

"For testing your installation run php tests/phpunit/phpunit.php extensions/Math/tests/ from your MediWiki home path."

...but what happened to the /tests folder? It does not appear under my installation.

<http://www.mediawiki.org/wiki/Manual:PHP_unit_testing> <https://doc.wikimedia.org/mediawiki-core/master/php/html/dirs.html>

Convert Existing LaTeX Documents into Wiki Markup
-------------------------------------------------

[StackOverflow—Convert LaTeX to MediaWiki Syntax](http://stackoverflow.com/questions/2029270/convert-latex-to-mediawiki-syntax)

MathJax in MediaWiki
--------------------

**UNFORTUNATELY, this extension has been DEPRECATED. I can't get the regular Math extension to render Mathjax correctly, so use [SimpleMathJax](http://www.mediawiki.org/wiki/Extension:SimpleMathJax) instead!**

[MediaWiki—Extension:Mathjax](http://www.mediawiki.org/wiki/Extension:MathJax)

<nomathjax>The Math extension requires that you utilize a math environment only by using \(\) tags, which are cute but much slower than the LaTeX default $...$ and $$...$$ tags.</nomathjax>

The MathJax extension brings a more standard LaTeX environment to MediaWiki! As an added bonus, your wiki won't explode if you already have and use the Math extension:

    "It doesn't matter if you have $wgUseTeX set to true or false. Extension:MathJax will take over rendering of the standard <math> rendering."

    require_once( "$IP/extensions/MathJax/MathJax.php" );
    /** There is a bug in Extension:MathJax with MediaWiki 1.19.0, 1.20.0 and 1.21.1
    *   If you are using any form of PHP caching on your wiki and you have setup
    *   your wiki to use variable caching like $wgMainCacheType = CACHE_ACCEL;
    *   you could encounter issues with rendering of formulas.
    *   If so uncomment the last line.
    */
    #$wgParserCacheType = CACHE_NONE;

Adding Extra LaTeX Packages
---------------------------

sudo apt-get texlive-full texlive-latex3 texlive-latex-recommended texlive-latex-extra To change how the rest of the wiki displays, try modifying the CSS: <http://www.mediawiki.org/wiki/Manual:Interface/Stylesheets>

For example: <http://wiki.graveslab.org/w/MediaWiki:Common.css>

You can even make your own custom user markup! $wgAllowUserCss = true <http://wiki.graveslab.org/w/MediaWiki:common.css>

To configure MathJax, play around with the config file: <http://docs.mathjax.org/en/v1.1-latest/configuration.html#configuring-mathjax>

For the MathJax extension, this file is called mwMathJaxConfig.js

To exclude MathJax from a block, use

    <nomathjax>

.

"Because MathJax starts its configuration process as soon as it is loaded, the configuration script must come before the script tag that loads MathJax.js itself. You do this by including a

<script>
with type="text/x-mathjax-config", whose content will be run when MathJax performs its configuration. Generally, this script will include a MathJax.Hub.Config() call to perform MathJax configuration, but it can also include other MathJax commands, such as registering signal actions, or any JavaScript commands that you want."

example:

<script type="text/x-mathjax-config">
The configuration options are here: <http://docs.mathjax.org/en/v1.1-latest/options/HTML-CSS.html>

example: "HTML-CSS": {scale: 200}

[Category:Wiki Setup](/Category:Wiki_Setup "wikilink")
