---
title: Jekyll for Static Sites
permalink: p/jekyll
layout: default
category: software
featured: true
---

## GitHub Pages Generates Sites With Jekyll

Jekyll is a tool called a "static site generator".  The goal of a static site generator is to effectively separator a site's content from its layout and style.

In Jekyll, content is stored in Markdown, a simple markup language designed for simplicity and readability.  The site's layout is built up from page templates using Markdown, HTML (including insertable reusable fragments), and a simple programming language called "liquid tags".  Each page, and the site overall, can have metadata stored in YAML ("Yet Another Markup Language") that can be used to select templates and define variables that are used to build the page.  When Jekyll is run, it processes the templates, tags, metadata, and content and generates HTML files that can be served by Jekyll itself or another webserver like `Apache` or `nginx`.

In 2016-04, GitHub announced they were [standardized on one Markdown engine, kramdown, for GitHub Pages][ghpages-kramdown].  Kramdown extends vanilla Markdown with some additional syntax, including [inline attribute lists][kramdown-ial] for assigning classes to block and inline elements without the use of HTML tags.


## Building a site with Jekyll

Jonathan McGlone's [Creating and Hosting a Personal Site on GitHub][mcglone-ghpages] is the best guide I've found so far, especially for someone who wants to take a totally custom ground-up approach and not just recycle a template.

The official documentation has [a page on customizing a static site built with Jekyll][jekyll-config] using options in the `_config.yml` file.  [YAML options can even be nested lists][jekyll-lists].

Many tutorials discuss how to configure your site as a blog using a _blogpost collection, but [the collections feature is flexible and powerful enough to implement all kinds of site structures][jekyll-collections].

Liquid tags are the key to fully utilizing Jekyll; they're discussed in-depth in [the Shopify documentation][liquid] (Shopify is a tool built on Jekyll).


## Academic Pages Using Jekyll

+ Nice!
  + http://drummondlab.org/
    + https://github.com/drummondlab/drummondlab.github.io
  + http://bedford.io/
    + https://github.com/blab/blotter
  + http://girke.bioinformatics.ucr.edu/
    + https://github.com/tgirke/tgirke.github.io
  + http://notebook.madsenlab.org/
    + https://github.com/mmadsen/lnraw
  + http://www.carlboettiger.info/
    + https://github.com/cboettig/labnotebook
  + http://scholarslab.org/
    + https://github.com/scholarslab/scholarslab.org
  + http://blog.evercodelab.com/
    + https://github.com/EvercodeLab/blog.evercodelab.com
+ Not Great
+ Unverified
  + http://primaresearch.org/
  + https://edwards.sdsu.edu/research/
  + https://waldronlab.github.io/
  + http://www.allanlab.org/
    + https://github.com/allanlab/allanlab
  + http://arfc.npre.illinois.edu/
    + http://kdhuff.npre.illinois.edu/
    + github.com/arfc/arfc.github.io
  + http://rglab.org/
    + https://github.com/RGLab/rglab.github.io
+ https://ccs-lab.github.io/
  + based on Trevor Bedford's bedford.io
    + https://github.com/blab/blotter
  + adopts stuff from Allan Drummond
    + https://github.com/drummondlab/drummondlab.github.io
  + repo must be private!
+ http://www.molpopgen.org/
  + repo: https://github.com/ThorntonLab/ThorntonLab.github.io
+ http://notebook.aaronwest.net/
  + "engineering notebook"
  + repo: https://github.com/aaronwest/aaronwest.github.io/


## Practical Use

### Alternatives to Jekyll

+ Hugo
  + http://www.carlboettiger.info/2017/04/19/migrating-to-hugo-and-blogdown/
+ Rails?
  + https://publiclab.org/
  + https://github.com/publiclab/plots2
+ Node
  + https://evercodelab.com/
  + https://github.com/EvercodeLab/evercodelab.com

### Gotchas

Avoid [problems with relative links](https://github.com/jekyll/jekyll/issues/332) by using <pre>{{ site.baseurl }}{{ post.url }}</pre> in Liquid scripts.


### Moving from Mediawiki

[Philip Ashlock's Mediawiki-to-Markdown converter](https://github.com/philipashlock/mediawiki-to-markdown) will convert your wiki's XML dumps directly to Markdown with frontmatter (or any one of a variety of other Pandoc-supported formats).

    http://www.nomachetejuggling.com/2012/05/15/personal-wiki-using-github-and-gollum-on-os-x/
    https://github.com/gollum/gollum
    https://github.com/philipashlock/mediawiki-to-markdown

    https://www.mediawiki.org/wiki/Manual:DumpBackup.php
    php dumpBackup.php --conf /var/www2/www-bsc/wiki/LocalSettings.php --full > dump.xml

    sudo apt-get install php5-cli

    curl -sS https://getcomposer.org/installer | php
    php composer.phar install

    getcomposer.org
    curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer

    php convert.php --filename=mediawiki.xml --output=export --indexes=true
    php convert.php --filename="../www-bsc.wiki/dump.xml" --output=export --indexes=true



    ## How It's Done

    THIS IS WHAT WE WANT:

    https://www.mediawiki.org/wiki/Manual:DumpBackup.php

    brandon@patientzero: /var/www2/wikis/wiki-bsc/maintenance$ php dumpBackup.php --current --conf /var/www2/wikis/wiki-bsc/LocalSettings.php > /home/brandon/backups/dump-bcwiki.xml

    can restrict by namespace (we want 0):

    https://www.mediawiki.org/wiki/Manual:Namespace

    php dumpBackup.php --current --filter=namespace:10 > templates.xml


    This tool sometimes chokes on nested tables, so you may have to do some manual cleanup!

    References:

    + https://docs.google.com/document/d/13g7Znpmt-uawgyNtxTrvirBidy6M52TNilFqoyOSyrE/edit#
    + https://docs.google.com/document/d/1wT4mRR-8O67I7CKksu10-j5c-6s40SZARbqSoDCXYLY/edit#
    + https://docs.google.com/document/d/1vApYi5CijrpawS9AkOpFoyv1jtDwthvy7QJxzEDs0BI/edit#


    ## mysqldump generates invalid xml


    mysqldump -h localhost -u wikiuser wiki_bsc | gzip > /home/brandon/backups/backup-wiki-bsc-$today.sql.gz

    mysqldump -h localhost -u wikiuser --xml wiki_bsc | gzip > /home/brandon/backups/backup-wiki-bsc-$today.xml.gz

    This yields garbage data!

        <field Field="user_touched" Type="binary(14)" Null="NO" Key="" Default="^@^@^@^@^@^@^@^@^@^@^@^@^@^@" Extra="" Comment="" />
        <field Field="user_token" Type="binary(32)" Null="NO" Key="" Default="^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@" Extra="" Comment="" />


    This problem is referenced elsewhere:

    + https://rpbouman.blogspot.com/2010/04/restoring-xml-formatted-mysql-dumps.html
    + https://bugs.mysql.com/bug.php?id=19745

    "mysqldump produces invalid xml when data contains blobs. It should  respect the hex-blob switch, but it is ignored."


## Resources

Jekyll guides

+ http://blog.evercodelab.com/from-posterous-to-octopress-plus-github-dot-pages/
+ http://svmiller.com/blog/2015/08/create-your-website-in-jekyll/
+ http://jlord.us/forkngo/
+ https://drjekyllthemes.github.io/
+ https://github.com/showcases/github-pages-examples

Other articles

+ https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/
+ https://jekyllrb.com/docs/github-pages/
+ https://24ways.org/2013/get-started-with-github-pages/
+ https://jekyllrb.com/docs/variables/
+ http://www.remotesynthesis.com/general/2015/10/02/advanced-jekyll-templates/
+ [Ten Simple Rules for Taking Advantage of Git and GitHub](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4945047/)
+ [Building a static website with Jekyll and GitHub Pages](https://programminghistorian.org/lessons/building-static-sites-with-jekyll-github-pages)
+ [What's This Engineering Notebook All About?](http://notebook.aaronwest.net/2015/08/17/engineering-notebook.html)
+ [Git/GitHub: A Primer for Researchers](https://datapub.cdlib.org/2014/05/05/github-a-primer-for-researchers/)




[ghpages-kramdown]: https://github.com/blog/2136-a-look-behind-our-decision-to-standardize-on-a-single-markdown-engine-for-github-pages
[kramdown-ial]: https://kramdown.gettalong.org/syntax.html#block-ials
[mcglone-ghpages]: http://jmcglone.com/guides/github-pages/
[jekyll-config]: https://jekyllrb.com/docs/configuration/
[jekyll-collections]: https://jekyllrb.com/docs/collections/
[jekyll-lists]: https://stackoverflow.com/questions/12761152/yaml-front-matter-for-jekyll-and-nested-lists
[liquid]: https://github.com/Shopify/liquid/wiki/Liquid-for-Designers
