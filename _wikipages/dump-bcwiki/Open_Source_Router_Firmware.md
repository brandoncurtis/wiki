---
title: Open Source Router Firmware
permalink: "/Open_Source_Router_Firmware/"
---

Asus RT-N56U
------------

[ASUS RT-N56U/N65U/N14U/N11P/AC51U custom firmware](https://code.google.com/p/rt-n56u/)

[RT-N56U Wiki: Common Tips](https://code.google.com/p/rt-n56u/wiki/CommonTips)

### Interrogating Clients

There are several options available to list the clients that are currently connected to a router running Linux-based firmware.

At the most basic level is [ARP](http://en.wikipedia.org/wiki/Address_Resolution_Protocol), the Address Resoluton Protocol. List the devices in the ARP cache (name, IP address, and MAC address) with `arp`. The cache is usually refreshed every minute or so, as defined in a file called `gc_stale_time`; search for this file with `find` `/` `-iname` `gc_stale_time`.

For more detailed status information, try `ip` `neighbor` from the [`iproute2`](http://www.linuxfoundation.org/collaborate/workgroups/networking/iproute2) networking toolset. In addition to listing the IP and MAC addresses, each device's current status ([REACHABLE, STALE, DELAY, &etc](http://linux-ip.net/html/ether-arp.html)) is included. When a device is disconnected, you can watch it traverse the statuses until it's dropped from the ARP cache.

If your router uses [dnsmasq](http://en.wikipedia.org/wiki/Dnsmasq) for DHCP (very many do), you can view the current list of static and dynamic leases in the file `dnsmasq.leases`; search for this file with `find` `/` `-iname` `dnsmasq.leases`. The list of leases is updated rapidly after device connection or disconnection. To see if the device 'bcurtis-motox' is currently connected, you could use something like `cat` `/tmp/dnsmasq.leases` `|` `grep` `bcurtis-motox`

### Waking Up Clients

Many devices support [Wake-On-LAN](http://en.wikipedia.org/wiki/Wake-on-LAN) (WOL), and can be woken up with a command sent over the network. In the RT-N56U firmware, this is accomplished with the `ether-wake` utility. To wake up the device with MAC address F4:6D:04:1F:02:1B, use `ether-wake` `-b` `-i` `br0` `F4:6D:04:1F:02:1B`

This can be especially fun when combined with scheduled tasks in [`crontab`](https://code.google.com/p/rt-n56u/wiki/CommonTips#Using_the_built-in_scheduler_(crond)). This code wakes up the device with MAC address F4:6D:04:1F:02:1B when the device 'bcurtis-motox' comes online:

    #!/bin/bash
    motox=$(arp | grep bcurtis-motox)
    if [ -n "$motox" ]; then
        ether-wake -b -i br0 F4:6D:04:1F:02:1B
    fi

### Building a Toolchain for Cross-Compilation

Entware is an Open-WRT tool, so it [was never intended to offer native compilation](http://www.snbforums.com/threads/using-entware-optware-on-stock-firmware.8715/):

> Is it possible to add a buildroot/gcc package to entware (also automake, autoconf, etc)? Because with optware you have that and i compile small things on the router itself (is faster than crosscompiling and trasnferring everytime)!
>
> In fact, Entware is OpenWRT, so no native compilation is provided. Not for now, not in future. A modern gcc eats too much memory for running on embedded devices. We may port it without any optimisations (-O2, -O3, -Os), but it will be useless.

Instead, you can set up a toolchain on another machine to cross-compile software for the router:

-   <https://bitbucket.org/padavan/rt-n56u/src/dec69145e70624036d12af8902febdcd96cebb75/toolchain-mipsel/readme.eng.txt?at=master&fileviewer=file-view-default>
-   <https://github.com/Entware/entware/wiki/How-to-add-a-new-package-or-rebuild-the-feed>

[Category:Software](/Category:Software "wikilink") __FORCETOC__