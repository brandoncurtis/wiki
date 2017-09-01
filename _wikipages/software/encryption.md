---
title: Encryption
permalink: p/encryption
layout: wikipage
category: software
---

* toc
{:toc}

----

## Keybase

Using the Keybase command line app

keybase pgp encrypt -m "message" connorgalleher
With GPG or another PGP program

You may import from Keybase to GPG easily and then perform whatever cryptographic actions you want.

    # using curl
    curl https://keybase.io/connorgalleher/key.asc | gpg --import

    # using `keybase pgp pull` which
    # imports to GPG key chain for you
    keybase follow connorgalleher
    keybase pgp pull connorgalleher

----

gpg --keyserver pgp.mit.edu --send-key connor.galleher@gmail.com

gpg --export-secret-keys -a 4D29CC3A > mykeys.key


## Signing Someone Else's Keys

https://www.debian.org/events/keysigning

gpg --list-keys -a connor
gpg --edit-key D3390744
gpg --keyserver keyserver.ubuntu.com --send-key 34E7001F
gpg --keyserver pgp.mit.edu --send-key 34E7001F
gpg --keyserver pgp.mit.edu --search-keys bgillespie
