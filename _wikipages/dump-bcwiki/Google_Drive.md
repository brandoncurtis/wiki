---
title: Google Drive
permalink: /Google_Drive/
---

Integration with Other Services
-------------------------------

### Google Keep Integration

This was [hinted at a long time ago](http://googlesystem.blogspot.com/2013/09/google-keep-to-integrate-with-google.html) (2013-09) but still hasn't materialized.

### Search Google Drive from the Chrome Omnibox

via: <http://goo.gl/3T762e>

"To enable search in Google Drive from the Omnibox, right click the omnibox and then click Manage Search engines and enter this data:

Name: Google Drive Keyword: Drive URL: [https://docs.google.com/?hl=en&tab=bo\#search/%s](https://docs.google.com/?hl=en&tab=bo#search/%s)

Now close the settings from the Omnibox and type "Drive" and hit TAB."

"I altered to work with my Google Apps domain as follows: <https://drive.google.com/a/><YOUR.DOMAIN.COM>/\#search/%s﻿"

"For specific searches, for years I've been using the following search engines I've added; works great:

-   ctrl+k: Google Search (Chrome built-in)
-   syt: [http://www.youtube.com/results?search_query=%s](http://www.youtube.com/results?search_query=%s) (syt: short for Search YouTube)
-   samz: [http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=%s&x=0&y=0](http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=%s&x=0&y=0)
-   sadb: [http://www.audible.com/search?advsearchKeywords=%s](http://www.audible.com/search?advsearchKeywords=%s)
-   sbbc: [http://search.bbc.co.uk/search?opensearch=all-1&q=%s](http://search.bbc.co.uk/search?opensearch=all-1&q=%s)
-   scn: [https://catch.com/m/\#?search=%s](https://catch.com/m/#?search=%s)
-   scb: [chrome://bookmarks/?\#q=%s](chrome://bookmarks/?#q=%s)
-   sety: [http://www.etymonline.com/index.php?term=%s](http://www.etymonline.com/index.php?term=%s)
-   sgb: [https://www.google.com/search?q=%s&btnG=Search+Books&tbm=bks&tbo=1&safe=active](https://www.google.com/search?q=%s&btnG=Search+Books&tbm=bks&tbo=1&safe=active)
-   sgd: [https://drive.google.com/\#search/%s](https://drive.google.com/#search/%s)
-   sgi: [https://www.google.com/search?tbm=isch&hl=en&q=%s](https://www.google.com/search?tbm=isch&hl=en&q=%s)
-   sg+: [https://plus.google.com/s/%s](https://plus.google.com/s/%s)
-   sgrm: [http://grammarist.com/search-results/?q=%s](http://grammarist.com/search-results/?q=%s)
-   shys: [http://www.howjsay.com/index.php?word=%s&submit=Submit](http://www.howjsay.com/index.php?word=%s&submit=Submit)
-   slc: [http://www.linkedin.com/csearch/results?type=companies&keywords=%s](http://www.linkedin.com/csearch/results?type=companies&keywords=%s)
-   slp: [http://www.linkedin.com/search/fpsearch?type=people&keywords=%s](http://www.linkedin.com/search/fpsearch?type=people&keywords=%s)
-   smw: [http://www.merriam-webster.com/dictionary/%s](http://www.merriam-webster.com/dictionary/%s)
-   sod: [http://oxforddictionaries.com/search/?region=uk&direct=1&q=%s](http://oxforddictionaries.com/search/?region=uk&direct=1&q=%s)
-   sref: [http://dictionary.reference.com/browse/%s](http://dictionary.reference.com/browse/%s)
-   swp: [http://en.wikipedia.org/w/index.php?title=Special:Search&search=%s](http://en.wikipedia.org/w/index.php?title=Special:Search&search=%s)
-   swq: [http://en.wikiquote.org/w/index.php?title=Special:Search&search=%s](http://en.wikiquote.org/w/index.php?title=Special:Search&search=%s)

Close Settings; in Omnibar, type assigned keyword; hit TAB; enter your search word; hit Enter."

unfortunately, this doesn't autocomplete—it loads the search results right inside Google Drive.

Omnidrive allows autocompletion: <https://chrome.google.com/webstore/detail/omnidrive/gpnikbcifngfgfcgcgfahidojdpklfia> "Do not consume memory when it's doing nothing thanks to Event pages."

    Wikipedia
    wiki
    http://en.wikipedia.org/wiki/Special:Search?search=%s

    Google Scholar
    scholar
    http://scholar.google.com/scholar?hl=en&q=%s&btnG=&as_sdt=1%2C5&as_sdtp=

    Digikey
    digikey
    http://www.digikey.com/product-search/en?x=0&y=0&lang=en&site=us&KeyWords=%s

    Ask Ubuntu
    ubuntu
    http://askubuntu.com/search?q=%s

    YouTube
    youtube
    http://www.youtube.com/results?search_query=%s&page={startPage?}&utm_source=opensearch

    NCBI PubMed
    pubmed
    http://www.ncbi.nlm.nih.gov/pubmed/?term=%s

Syncing Google Drive with the Desktop
-------------------------------------

### Drive App

[Google Drive Ap for Linux @ Distracts Others](http://blog.brandoncurtis.com/2015/04/google-drive-app-for-linux.html)

    ----
    http://www.howtogeek.com/196635/an-official-google-drive-for-linux-is-here-sort-of-maybe-this-is-all-well-ever-get/

    sudo apt-get install golang git mercurial

    go get github.com/rakyll/drive

    drive help
    drive init
    drive push
    drive pull

    ----
    https://github.com/rakyll/drive

    "This project is under new maintenance because I am now too busy to maintain it. Find the latest and updated code at https://github.com/odeke-em/drive"

    ----
    https://github.com/odeke-em/drive

    ----
    brandon@D105:~/bin$ GOPATH=/home/brandon/bin/go
    brandon@D105:~/bin$ export GOPATH
    brandon@D105:~/bin$ go get github.com/odeke-em/drive
    package github.com/odeke-em/drive
        imports github.com/odeke-em/drive
        imports github.com/odeke-em/drive: no buildable Go source files in /home/brandon/bin/go/src/github.com/odeke-em/drive
    ----
    from README.md:

    $ go get -u github.com/odeke-em/drive/cmd/drive
    $ drive init ~/gdrive
    $ cd ~/gdrive
    $ sudo ln -s /home/brandon/bin/go/bin/drive /usr/local/bin/drive

    $ drive list
    $ drive stat
    ----
    on curtis-desktop-01:

    sudo apt-get install golang git mercurial
    GOPATH=/home/brandon/bin/go
    export GOPATH
    go get -u github.com/odeke-em/drive/cmd/drive
    mkdir Drive
    sudo ln -s /home/brandon/bin/go/bin/drive /usr/local/bin/drive
    ----
    http://unix.stackexchange.com/questions/22494/copy-file-to-xclip-and-paste-to-firefox

    sudo apt-get install xclip

    sudo ln -s /home/brandon/bin/go/bin/drive /usr/local/bin/drive
    ----
    /home/brandon/WWServer/People/Brandon/Music/!BC_Music/

### OCAML Fuse in Ubuntu

Mount Google Drive in Ubuntu with google-drive-ocamlfuse

via: <http://www.webupd8.org/2013/09/mount-google-drive-in-linux-with-google.html>

sudo add-apt-repository ppa:alessandro-strada/ppa sudo apt-get update sudo apt-get install google-drive-ocamlfuse

google-drive-ocamlfuse

FAILED. Server not responding!

Went here to create OAuth2 credentials: <https://developers.google.com/console/help/#creatingdeletingprojects>

URL: \#\#\#.apps.googleusercontent.com Client secret: xxx

google-drive-ocamlfuse -client_id \#\#\#.apps.googleusercontent.com -client_secret xxxx

SUCCESS. Authenticated!

mkdir ~/gdrive

google-drive-ocamlfuse ~/gdrive

sudo nano ~/.gdfuse/default/config

add to startup apps: google-drive-ocamlfuse -debug /path/to/gdrive

You can even use -label in the authentication step to sync multiple accounts!

Google Spreadsheets
-------------------

### Conditional Formatting with Functions

This is amazingly useful and [amazingly simple.](https://support.google.com/docs/answer/78413?hl=en)

### Working With Arrays

To apply a non-array function to an array, enclose the non-array function in 'ARRAYFORMULA()'.

For example, to return 'TRUE' if any cell in the array A1:C10 is blank:

=OR(ARRAYFORMULA(ISBLANK(A1:C10)))

### Function Fill-Down

Highlight the cells you wish to fill from, then use Shift-Down or Ctrl-Shift-Down to select the cells you with to fill into. Hit Ctrl-D to fill down! You can use [a similar technique and Ctrl-R](http://stackoverflow.com/questions/12621842/fill-down-google-apps-script-for-spreadsheets) to fill right.

Saving a Document in Multiple Folders
-------------------------------------

In Old Google Drive (2013), you could shift-click and control-click to place a document in multiple folders; in New Google Drive (2014), you'll need to [select the file and hit 'Shift-Z' to bring up the 'Add To Folder' dialog](http://www.alicekeeler.com/teachertech/2014/07/11/new-google-drive-saving-a-document-in-multiple-folders/).

Hosting a Website
-----------------

via Google Support: \[//support.google.com/drive/answer/2881970?hl=en Host webpages with Drive\]

This feature is **not available in \[//support.google.com/drive/answer/6021328 New Google Drive\]** (2014.09.23).

To host a webpage with Drive:

1.  Create a new folder in Drive and share it as "Public on the web."
2.  Upload your HTML, Javascript, and CSS files to this folder.
3.  Open the HTML file and click Open in the bottom-right corner.
4.  Click the "Preview" button in the toolbar.
5.  Share the URL that looks like "www.googledrive.com/host/..." from the preview window and anyone can view your web page.

Drive API
---------

<http://campus.codeschool.com/courses/discover-drive/intro>

[Category:Software](/Category:Software "wikilink")