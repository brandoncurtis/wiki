---
title: Huginn
permalink: /Huginn/
---

Introduction
------------

Installation

-   <https://gist.github.com/mjhea0/b6b58eefc38985380ff9>
-   <https://github.com/cantino/huginn/wiki/Novice-setup-guide>
-   <https://github.com/cantino/huginn#quick-start>

Huginn, the opensource IFTTT – Yahoo! Pipes mix

-   <http://blog.pragmasphere.com/2014/06/10/huginn-the-opensource-iftttyahoo-pipes-mix/>

Open Source Project Mimics Yahoo Pipes on Your Own Machine

-   <http://www.wired.com/2013/03/hugin/>

Never Forget Your Umbrella Again, With Huginn

-   <http://blog.andrewcantino.com/blog/2014/01/12/never-forget-your-umbrella-again-with-huginn/>

Setting Up Ruby
---------------

install Ruby with rbenv

-   <https://www.digitalocean.com/community/tutorials/how-to-install-ruby-on-rails-with-rbenv-on-ubuntu-14-04>

<!-- -->

    sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties libffi-dev

    cd
    git clone git://github.com/sstephenson/rbenv.git .rbenv
    echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
    echo 'eval "$(rbenv init -)"' >> ~/.bashrc

    git clone git://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
    echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc
    source ~/.bashrc

    rbenv install -v 2.2.3
    rbenv global 2.2.3
    ruby -v

    echo "gem: --no-document" > ~/.gemrc
    gem install bundler
    gem install rails
    rbenv rehash
    rails -v

    sudo add-apt-repository ppa:chris-lea/node.js
    sudo apt-get update
    sudo apt-get install nodejs

    gem install gollum
    gem install redcarpet

Creating the Plasma Medicine Feed Aggregator
--------------------------------------------

### The Feeds - ADDED

PLoS ONE

-   <http://www.plosone.org/article/feed/search?unformattedQuery=everything%3A%22atmospheric+plasma%22>
-   <http://www.plosone.org/article/feed/search?unformattedQuery=everything%3A%22atmospheric+pressure+plasma%22>
-   <http://www.plosone.org/article/feed/search?unformattedQuery=everything%3A%22air+plasma%22>

Plasma Processes and Polymers

-   <http://onlinelibrary.wiley.com/journal/10.1002/(ISSN)1612-8869>
-   <http://onlinelibrary.wiley.com/rss/journal/10.1002/(ISSN)1612-8869>

Journal of Physics D: Applied Physics

-   <http://iopscience.iop.org/0022-3727/>
-   <http://iopscience.iop.org/0022-3727/?rss=1>

Journal of the Korean Physical Society

-   <http://link.springer.com/journal/40042>
-   <http://link.springer.com/search.rss?facet-content-type=Article&facet-journal-id=40042&channel-name=Journal+of+the+Korean+Physical+Society>

Journal of Vacuum Science & Technology A: Vacuum, Surfaces, and Films

-   <http://scitation.aip.org/content/avs/journal/jvsta>
-   <http://scitation.aip.org/rss/content/avs/journal/jvsta/latestarticles?fmt=rss>

Journal of Vacuum Science & Technology B: Microelectronics and Nanometer Structures

-   <http://scitation.aip.org/content/avs/journal/jvstb>
-   <http://scitation.aip.org/rss/content/avs/journal/jvstb/latestarticles?fmt=rss>

Plasma Sources Science and Technology

-   <http://iopscience.iop.org/0963-0252/>
-   <http://iopscience.iop.org/0963-0252/?rss=1>

Japanese Journal of Applied Physics

-   <http://jjap.jsap.jp/>
-   <http://jjap.jsap.jp/rss/jjapPt1.xml>

The European Physical Journal - Applied Physics

-   <https://journals.cambridge.org/action/displayJournal?jid=JAP>
-   <http://journals.cambridge.org/data/rss/feed_JAP_rss_2.0.xml>
-   <http://journals.cambridge.org/data/rss/feed_JAP_FirstView_rss_2.0.xml>

Free radical biology & medicine

-   <http://www.journals.elsevier.com/free-radical-biology-and-medicine/>
-   <http://rss.sciencedirect.com/publication/science/08915849>

Applied Surface Science

-   <http://www.journals.elsevier.com/applied-surface-science/>
-   <http://rss.sciencedirect.com/publication/science/01694332>

Physical Review E

-   <https://journals.aps.org/pre/>
-   <http://feeds.aps.org/rss/tocsec/PRE-Plasmaphysics.xml>

Journal of bioscience and bioengineering

-   <http://www.journals.elsevier.com/journal-of-bioscience-and-bioengineering/>
-   <http://rss.sciencedirect.com/publication/science/13891723>

Plasma Chemistry and Plasma Processing

-   <http://www.springer.com/chemistry/inorganic+chemistry/journal/11090>
-   <http://www.springer.com/physics/rssfeed?4-10100-820-0-0>

Journal of Plasma Physics

-   <https://journals.cambridge.org/action/displayJournal?jid=PLA>
-   <http://journals.cambridge.org/data/rss/feed_PLA_FirstView_rss_2.0.xml>

### The Feeds - TO ADD