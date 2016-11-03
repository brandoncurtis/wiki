---
layout: default
category: software
title: Jekyll for Static Sites
permalink: p/jekyll
---

## Building a site with Jekyll

Jonathan McGlone's [Creating and Hosting a Personal Site on GitHub](http://jmcglone.com/guides/github-pages/) is the best guide I've found so far, especially for someone who wants to take a totally custom ground-up approach and not just recycle a template.

The official documentation has [a page on customizing a static site built with Jekyll](https://jekyllrb.com/docs/configuration/) using options in the _config.yml file.  [YAML options can even be nested lists](https://stackoverflow.com/questions/12761152/yaml-front-matter-for-jekyll-and-nested-lists).

Many tutorials discuss how to configure your site as a blog using a _blogpost collection, but [the collections feature is flexible and powerful enough to implement all kinds of site structures](https://jekyllrb.com/docs/collections/).

Liquid tags are the key to fully utilizing Jekyll; they're discussed in-depth in [the Shopify documentation](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers) (Shopify is a tool built on Jekyll).


## Gotchas

Avoid [problems with relative links](https://github.com/jekyll/jekyll/issues/332) by using {{ site.baseurl }}{{ post.url }} in Liquid scripts.

## Moving from Mediawiki

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


## News

In 2016-04, GitHub announced they were [standardized on one Markdown engine, kramdown, for GitHub Pages](https://github.com/blog/2136-a-look-behind-our-decision-to-standardize-on-a-single-markdown-engine-for-github-pages).

## Resources

+ https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/
+ https://jekyllrb.com/docs/github-pages/
+ https://24ways.org/2013/get-started-with-github-pages/
+ https://jekyllrb.com/docs/variables/
+ http://www.remotesynthesis.com/general/2015/10/02/advanced-jekyll-templates/
