---
layout: default
title: Bittorrent
permalink: p/bittorrent
category: software
---


Creating a Torrent
------------------

From Transmission or another bittorrent client, you can click 'new' or 'create' to make your own torrent. All you need to get started is the file you want to torrent! [Thomas Vanhoutte](https://thomas.vanhoutte.be/miniblog/torrent-tracker-2016/) has a list of the top trackers to use.

Advertising Your Torrent
------------------------

Create an account on [The Pirate Bay](https://thepiratebay.se) and upload your torrent to publicly advertise it.

Configuring Transmission
------------------------

use apt-file to look for files!

-   <https://wiki.archlinux.org/index.php/Transmission>
-   <https://trac.transmissionbt.com/wiki/UnixServer/Debian>
-   <https://trac.transmissionbt.com/wiki/EditConfigFiles>
-   <https://wiki.openwrt.org/doc/uci/transmission>
-   <http://www.webupd8.org/2009/12/setting-up-transmission-remote-gui-in.html>
-   <https://wiki.debian.org/BitTorrent/Transmission>
-   <https://help.ubuntu.com/community/TransmissionHowTo>
-   <https://trac.transmissionbt.com/wiki/EditConfigFiles>
-   <http://rpm.pbone.net/index.php3/stat/45/idpl/33406085/numer/1/nazwa/transmission-remote>
-   <https://trac.transmissionbt.com/wiki/EnvironmentVariables>
-   <https://trac.transmissionbt.com/wiki/ConfigFiles>
-   <http://askubuntu.com/questions/276649/where-is-the-settings-json-file-stored-for-transmission>

Bittorrent CLI
--------------

    https://trac.transmissionbt.com/wiki/ConfigFiles

    If you want to swap between the two applications, all you have to do is pass in a different config directory with the -g command-line option. For example, to have the daemon pick up where the gtk+ client left off, run transmission-daemon -g ~/.config/transmission

    http://askubuntu.com/questions/439950/how-do-i-stop-transmission-daemon

    http://askubuntu.com/questions/251797/transmission-daemon-keeps-resetting
    ----
    view transmission status through cli
    http://askubuntu.com/questions/335511/view-transmission-status-through-cli

    transmission-remote -n transmission:transmission -st
    ----

        "rpc-authentication-required": false,
        "rpc-bind-address": "0.0.0.0",
        "rpc-enabled": true,
        "rpc-password": "{d39ca584ab988e5995b580d03c9feb5b8a3a2de2D54JfA1O",
        "rpc-port": 9091,
        "rpc-url": "/transmission/",
        "rpc-username": "",
        "rpc-whitelist": "127.0.0.1",
        "rpc-whitelist-enabled": true,

        "rpc-authentication-required": false,
        "rpc-bind-address": "0.0.0.0",
        "rpc-enabled": true,
        "rpc-password": "{06e9723d3d7c8212d9c873eb09b7679c9de44af31DKQpKVG",
        "rpc-port": 9091,
        "rpc-url": "/transmission/",
        "rpc-username": "",
        "rpc-whitelist": "127.0.0.1",
        "rpc-whitelist-enabled": true,

    ----

    brandon@D094:~$ nano .config/transmission/settings.json
    brandon@D094:~$ ps aux | grep trans
    brandon  13912  0.8  0.1 2186232 7436 ?        Ssl  21:06   0:00 transmission-daemon -g /home/brandon/.config/transmission
    brandon  13978  0.0  0.0  15936   936 pts/9    S+   21:07   0:00 grep --color=auto trans
    brandon@D094:~$ kill 13912
    brandon@D094:~$ nano .config/transmission/settings.json
    brandon@D094:~$ nano .config/transmission-daemon/settings.json
    brandon@D094:~$ transmission-daemon -g ~/.config/transmission
    brandon@D094:~$ transmission-remote -n transmission:transmission -st

    CURRENT SESSION
      Uploaded:   None
      Downloaded: None
      Ratio:      None
      Duration:   6 seconds (6 seconds)

    TOTAL
      Started 6 times
      Uploaded:   41.59 GB
      Downloaded: 30.72 GB
      Ratio:      1.3
      Duration:   3 days, 20 hours (332231 seconds)
