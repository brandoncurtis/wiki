---
template: default
title: File Sync Software
permalink: p/file-sync
category: software
---

rsync
-----

<https://www.digitalocean.com/community/tutorials/how-to-use-rsync-to-sync-local-and-remote-directories-on-a-vps>

    man rsync is your friend!
    -a  archive; equals -rlptgoD
    -r  recurse into directories
    -l  copy symlinks as symlinks
    -p  preserve permissions
    -t  preserve modification times
    -g  preserve group
    -o  preserve owner (super-user only!)
    -D  preserve device and special files (super-user only!); equals –devices –special

    Other good ones to know, especially if you’re syncing to another r/w machine and not just pushing to a read-only backup:
    -v  verbose
    -L  transform symlink into referent file/dir
    -h  human-readable numbers
    -u  update; skip files that are newer on the receiver
    -c  skip based on checksum, not mod-time & size
    -P  progress bar; keep partially transferred files; equals –partial –progress

    For your purpose, I typically use:
    rsync -rLptgoDPhu

    If you don’t want to sync symlinked stuff, then:
    rsync -aPhu

Bittorrent Sync
---------------

Finally, a no-cost and secure tool for transferring terabytes of data between your computers... without ever touching The Cloud!

Check out news and use cases on the [Blog](http://blog.bittorrent.com/tag/bittorrent-sync/:Bittorrent).

This is a fantastic article on implementing a backup system with Bittorrent sync: [The Modern Scientist—Torrential File Synchronization](http://themodernscientist.com/posts/2014/2014-02-06-torrential_file_synchronization/).

Folder Sync Pro
---------------

A distributed file synchronization client for Mac and Windows. [$10 per client](http://www.greenworldsoft.com/sync-folders-pro-help.php:Costs).

[Category:Software](/Category:Software "wikilink")
