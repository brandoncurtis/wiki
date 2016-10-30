---
title: Virtual Private Network (VPN)
permalink: /Virtual_Private_Network_(VPN)/
---

How To

-   <https://www.linode.com/docs/networking/vpn/>
-   <https://www.linode.com/docs/networking/ssh/setting-up-an-ssh-tunnel-with-your-linode-for-safe-browsing>
-   <https://feeding.cloud.geek.nz/posts/creating-a-linode-based-vpn-setup-using_openvpn_on_debian_or_ubuntu/>
-   <https://www.linode.com/docs/networking/ssh/setting-up-an-ssh-tunnel-with-your-linode-for-safe-browsing>
-   <https://www.chromium.org/developers/design-documents/network-stack/socks-proxy>

<!-- -->

    ssh -D 12345 bc
    chromium-browser --proxy-server="socks://localhost:12345" --host-resolver-rules="MAP * ~NOTFOUND , EXCLUDE localhost"

Verify that it's working:

    chrome://net-internals/#proxy
    chrome://net-internals/#dns

About

-   <https://news.ycombinator.com/item?id=4483554>
-   <http://lifehacker.com/5940565/why-you-should-start-using-a-vpn-and-how-to-choose-the-best-one-for-your-needs>
-   <https://www.reddit.com/r/VPN/comments/2i86le/i_setup_my_own_vpn_with_linode/>

GPG over SOCKS Proxy
--------------------

-   <http://quack1.me/gpg_proxy_socks-en.html> (didn't work for me)
-   <https://sourceforge.net/p/enigmail/forum/support/thread/5636959c/> (someone with the same issue)
-   <https://lists.gnupg.org/pipermail/gnupg-users/2002-April/012692.html>
-   <https://lists.gnupg.org/pipermail/gnupg-users/2002-April/012692.html>
-   <https://lists.gnupg.org/pipermail/gnupg-devel/2012-September/026919.html>
-   <https://trac.torproject.org/projects/tor/ticket/6940#comment:26>

<!-- -->

    o as a pointer to others with a recent gpg version and linked against
    curl (with Debian or Ubuntu package gnupg-curl) - this should be safe
    for use with Tor:

    gpg --keyserver-options http-proxy=socks5-hostname://127.0.0.1:9050
    --search jacob at appelbaum.net

    I haven't yet found a machine where it worked but in theory it should
    work and not leak DNS.

    I'd still think a patch to set --socks-proxy=127.0.0.1:9050 would be
    useful as we could ensure SOCKS is actually in use or able to be used at
    all.

try tsocks, proxychains?

<http://askubuntu.com/questions/583797/how-to-set-a-proxy-for-terminal>

    sudo -H gedit /etc/profile.d/proxy.sh

    export http_proxy=http://username:password@proxyhost:port/
    export ftp_proxy=http://username:password@proxyhost:port/
    export telnet_proxy=http://username:password@proxyhost:port/

-   <http://askubuntu.com/questions/47379/how-to-use-a-proxy-on-the-command-line>
-   <http://superuser.com/questions/262956/how-to-invoke-a-command-using-specific-proxy-server>
