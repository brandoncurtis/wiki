---
title: Randomness
permalink: "/Randomness/"
---

Software Random Number Generation
---------------------------------

### Bash Shell

-   <http://en.wikipedia.org/wiki//dev/random>

On a Linux system and want to generate a nice string of random printable characters? [Courtesy of StackExchange](http://unix.stackexchange.com/questions/114878/reading-from-dev-random-does-not-produce-any-data), you can do it like this:

&lt;code&gt;&lt; /dev/random stdbuf -o0 tr -cd '\[:graph:\]'</code>

### Python

-   <https://docs.python.org/2/library/random.html>

Hardware Random Number Generation
---------------------------------

-   <http://en.wikipedia.org/wiki/Hardware_random_number_generator>
-   <http://en.wikipedia.org/wiki/Randomness_extractor>

Hardware-based RNGs are untrustworthy because chip makers have colluded with the government to install cryptographic backdoors:

-   <http://arstechnica.com/security/2013/12/we-cannot-trust-intel-and-vias-chip-based-crypto-freebsd-developers-say/>
-   <http://arstechnica.com/security/2013/09/stop-using-nsa-influence-code-in-our-product-rsa-tells-customers/>
-   <http://bits.blogs.nytimes.com/2013/09/10/government-announces-steps-to-restore-confidence-on-encryption-standards/?_r=0>
