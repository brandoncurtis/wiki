---
title: MediaWiki Setup Memcached
permalink: "/MediaWiki_Setup_Memcached/"
---

MediaWiki performance can be improved on large, high-traffic sites by installing and enabling memchached. See [Mediawiki: Memcached](http://www.mediawiki.org/wiki/Memcached) for details.

Installing memcached
--------------------

`sudo` `apt-get` `install` `memcached`

`memcached` `-d` `-l` `127.0.0.1` `-p` `11211` `-m` `64`

(to run in daemon mode, accessible only via loopback interface, on port 11211, using up to 64MB of memory)

To enable, add this to LocalSettings.php:

    $wgMainCacheType = CACHE_MEMCACHED;
    $wgParserCacheType = CACHE_MEMCACHED; # optional
    $wgMessageCacheType = CACHE_MEMCACHED; # optional
    $wgMemCachedServers = array( "127.0.0.1:11211" );

[Category:Wiki Setup](/Category:Wiki_Setup "wikilink")
