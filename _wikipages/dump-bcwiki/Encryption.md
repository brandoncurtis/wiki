---
layout: default
title: Encryption
permalink: p/encryption
category: software
---

Secure your communications with end-to-end encryption.

GnuPG (GPG
----------

    keybase pgp pull
    gpg --refresh-keys
    gpg --list-keys <key>
    gpg --list-sigs
    gpg --keyserver pgp.mit.edu --send-keys <key>
    gpg --edit-key <key>

-   <https://kb.iu.edu/d/awiu>
-   <http://irtfweb.ifa.hawaii.edu/~lockhart/gpg/gpg-cs.html>
-   <https://www.gnupg.org/documentation/manuals/gnupg/Operational-GPG-Commands.html>

Keybase
-------

    (13:35:28) BC: re:encryption keys
    (13:36:26) BC: you need keys to sign e.g. Ubuntu PPAs and repo contributions
    (13:37:09) BC: I am just getting set up for it, but it's generally considered good policy to sign your commits on e.g. Github
    (13:37:13) BC: and some projects require it
    (13:38:53) BC: key-based proofs are the best form of proof-of-identity for any kind of account
    (13:39:41) BC: if you told me you were Satoshi Nakamoto, I would ask you to sign that statement with a private key paired to one of Satoshi's known public keys
    (13:40:08) BC: and if you did it, I would pretty much believe that you were
    (13:41:08) BC: if you want to unequivocally prove that you own digital real estate (identities, DNS zones, sites), key-based proofs are the way to go
    (13:43:41) BC: some circles have used key-based proofs to build pretty expansive webs of trust https://en.wikipedia.org/wiki/Web_of_trust
    (13:44:47) BC: keypair encryption can be used to sign (proof-of-sender) and encrypt (privileged receiver) any string of bits
    (13:44:52) BC: any file, any message
    (13:45:10) BC: if you encrypt something with my public key, my private key is required for decryption
    (13:45:24) BC: and if you sign with your private key, I can verify the signature with your public key
    (13:46:12) BC: most email clients have a toolkit for signing and encrypting messages with trusted recipients https://support.mozilla.org/en-US/kb/digitally-signing-and-encrypting-messages
    (13:47:18) BC: so what Keybase does is, take all of this functionality that usually requires a ton of shell jockeying and:
    (13:48:51) BC:
    • simplify it under a convenient wrapper script
    • publicize it with public profiles powered by key-based identity proofs
    • reinforce it by announcing the key-based identity proof chain on the bitcoin blockchain
    (13:50:49) BC: and in alpha...
    • extend it to a globally secure filesystem with straightforward handling of permissions, automatic signing and encryption, and a publicly-facing publishing front-end at https://keybase.pub/
    (13:51:24) BC: https://brandoncurtis.keybase.pub/
    (13:51:37) BC: https://keybase.pub/brandoncurtis/index.md
    (13:51:56) BC: it's written in markdown: https://brandoncurtis.keybase.pub/index.md
    (13:52:41) BC: (currently limited to 10GB of free storage, but it's in alpha and very much a work in progress)
    (13:53:15) BC: Keybase was built by two very talented founders of OKCupid, the algorithmic dating site
    (13:53:53) BC: the above isn't even all of the cool stuff, which is kind of insane.
    (13:54:07) BC: for instance, I've already shared a signed, encrypted folder with you
    (13:54:17) BC: it's tied to your Github account
    (13:55:03) BC: and once you've cryptographically proved that identity, it will automatically re-key the folder and you'll have access
    (13:56:23) BC: this whole thing will also provide the infrastructure for building truly insane applications
    (14:09:00) BC: https://goo.gl/photos/BWzHWBT1MCfhTyMAA
    (14:10:13) BC: for instance, it has a feature which enables you to 'track' a user and snapshot their keys and identity proofs
    (14:10:43) BC: if anything changes, operations using the cached credentials will fail

References
----------

Pidgin OTR

-   <http://otr.cypherpunks.ca/>
-   <https://help.riseup.net/en/security/message-security/otr>
-   <http://en.wikipedia.org/wiki/Off-the-Record_Messaging>
-   <http://en.wikipedia.org/wiki/Socialist_millionaire>

Alternatives

-   <https://micahflee.com/2013/02/using-gajim-instead-of-pidgin-for-more-secure-otr-chat/>

[Category:Software](/Category:Software "wikilink") __FORCETOC__
