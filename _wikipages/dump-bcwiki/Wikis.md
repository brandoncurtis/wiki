---
title: Wikis
permalink: p/wikis
layout: wikipage
category: software
---

__FORCETOC__

GitHub Wiki
-----------

### Installing Gollum Locally

-   <http://www.nomachetejuggling.com/2012/05/15/personal-wiki-using-github-and-gollum-on-os-x/>
-   <https://github.com/gollum/gollum>
-   <https://github.com/philipashlock/mediawiki-to-markdown>
-   <https://www.mediawiki.org/wiki/Manual:DumpBackup.php>

php dumpBackup.php --conf /var/www2/www-bsc/wiki/LocalSettings.php --full &gt; dump.xml

    sudo apt-get install php5-cli

    curl -sS https://getcomposer.org/installer | php
    php composer.phar install

    getcomposer.org
    curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer

    php convert.php --filename=mediawiki.xml --output=export --indexes=true
    php convert.php --filename="../www-bsc.wiki/dump.xml" --output=export --indexes=true

try this for mediawiki to gollum: <https://github.com/brandonheller/mediawiki_to_gollum>

“The internal and external link formats that Gollum uses before WikiCloth parses the MediaWiki require a few changes, so the first script, change_mediawiki_links.py, does this conversion automatically when given an input file. The second script, split_by_headers.py, takes one big MediaWiki page and splits it by headers, plus generates a TOC automatically on the home page.”

MediaWiki -- gem install wikicloth

### References

-   <https://guides.github.com/features/wikis/>

------------------------------------------------------------------------

-   <https://help.github.com/categories/wiki/>

------------------------------------------------------------------------

-   <https://help.github.com/articles/about-github-wikis/>

"With wikis, you can write content just like everywhere else on GitHub. We use our open-source Markup library to convert different formats into HTML, so you can choose to write in Markdown, RST, Textile, or any other supported format when you craft wiki pages."

"Wikis can be edited directly on GitHub, or you can work with a text editor offline and simply push your changes. Wikis are collaborative by design. By default, every user can make changes to public wikis, but you can configure this to be enabled only for collaborators on your repository."

------------------------------------------------------------------------

Adding and editing wiki pages locally

-   <https://help.github.com/articles/adding-and-editing-wiki-pages-locally/>

"The filename determines the title of your wiki page. You can use the \\ character to escape special characters, such as spaces and punctuation, from the filename."

"If you create a file named _Footer. or _Sidebar., we'll use them to populate the footer and sidebar of your wiki, respectively."

------------------------------------------------------------------------

Making GitHub More Open: Git-backed Wikis

-   <https://github.com/blog/699-making-github-more-open-git-backed-wikis>

"Each wiki is a Git repository, so you're able to push and pull them like anything else. Each wiki respects the same permissions as the source repository. Just add ".wiki" to any repository name in the URL, and you're ready to go."

"We're also releasing Gollum, the same ruby library that powers GitHub Wikis. Gollum provides a ruby API for accessing and modifying your content, and also includes a small Sinatra web server. Clone the demo wiki to see what's available, or check out the Gollum readme for more detailed information."

------------------------------------------------------------------------

Personal Wiki using GitHub and Gollum on OS X

-   <http://www.nomachetejuggling.com/2012/05/15/personal-wiki-using-github-and-gollum-on-os-x/>

"Gollum is a Ruby-based wiki server that runs completely self-contained (you don't need to install PHP or a database) and is backed by Git. I use a Git repo cloned off a private GitHub repository for sync functionality."

"Gollum stores each wiki page in a separate file and uses a very simple markdown syntax for them all. There are no database files being shared or single-file indexes, so a conflict can only arise by editing the same wiki page, in approximately the same place. Otherwise Git will be able to merge the files and handle things without intervention. So far, I have not actually gotten a merge conflict that needed to be dealt with manually, so the windows seem small enough."

Federated Wikis
---------------

-   <http://fed.wiki.org/view/welcome-visitors>
-   <http://blog.jonudell.net/2015/01/22/a-federated-wikipedia/>
-   <https://github.com/WardCunningham/Smallest-Federated-Wiki>
-   <https://en.wikipedia.org/wiki/Smallest_Federated_Wiki>
-   <http://www.wired.com/2012/07/wiki-inventor/>

[Category:Software](/Category:Software "wikilink")
