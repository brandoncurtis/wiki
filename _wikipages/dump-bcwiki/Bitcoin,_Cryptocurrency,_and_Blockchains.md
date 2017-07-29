---
title: Bitcoin Cryptocurrency and Blockchains
permalink: "/Bitcoin_Cryptocurrency_and_Blockchains/"
---

[thumbnail|the Bitcoin logo|200px](/File:bitcoin-logo.png "wikilink")

Running a Bitcoin Node in Ubuntu
--------------------------------

### Full Node Installation

(instructions via <https://bitcoin.org/en/full-node>)

First, add the Personal Package Archive (PPA) for bitcoin software:

    sudo apt-add-repository ppa:bitcoin/bitcoin
    sudo apt-get update
    sudo apt-get install bitcoind

Before using the Bitcoin Core daemon, bitcoind, you need to create its configuration file with a user name and password:

    mkdir ~/.bitcoin
    touch ~/.bitcoin/bitcoin.conf
    chmod 600 ~/.bitcoin/bitcoin.conf

Run `bitcoind` to generate a unique "rpcpassword". Copy "rpcuser" and "rpcpwassword" into your configuration file:

    echo rpcuser=bitcoinrpc >> ~/.bitcoin/bitcoin.conf
    echo rpcpassword=XXXXXX >> ~/.bitcoin/bitcoin.conf

Now you can start Bitcoin Core daemon with `bitcoind` `-daemon`.

To start the bitcoin node daemon when Ubuntu boots, edit your crontab file with `crontab` `-e` and add `@reboot` `bitcoind` `-daemon` to a new line at the end of the file.

Congratulations, you're a node on the bitcoin network! Over the coming hours, the bitcoin daemon will download something like 80GB of blockchain files to your ~/.bitcoin directory. If you want to store this on a different hard drive, just stop the bitcoin daemon with `bitcoin-cli` `stop`, move the .bitcoin folder to the new drive, and use `ln` `-s` to create a symlink at ~/.bitcoin that points to folder's new location.

### Node Status

    bitcoin-cli getinfo     get the number of connected peers
    bitcoin-cli getblockcount   get total number of blocks retrieved

Installing a Bitcoin Wallet
---------------------------

Armory is a favorite bitcoin wallet among power users, but note that it's currently undergoing [a development leadership change](https://bitcointalk.org/index.php?topic=1351792.0).

-   <https://www.bitcoinarmory.com/download/>
-   <https://en.bitcoin.it/wiki/Armory>

You can buy, sell, and store bitcoin at e.g. [Coinbase](https://coinbase.com) and easily transfer bitcoin from Coinbase to your local wallet.

MAKE CERTAIN to create digital and paper backups of your Armory wallet to prevent your bitcoin from becoming unrecoverable in the event of a hard drive failure or accidental file deletion.

Accepting Bitcoin on your Website
---------------------------------

[How To Accept Bitcoins On Your Blog With No Code](http://gary-rowe.com/agilestack/2012/01/09/how-to-accept-bitcoins-on-your-blog-with-no-code/)

Transaction Time
----------------

[Bitcoin Average Transaction Confirmation Time](https://www.quandl.com/data/BCHAIN/ATRCT-Bitcoin-Average-Transaction-Confirmation-Time)

[Breaking the 10 Minute Confirmation Barrier"](https://blog.blockcypher.com/we-broke-the-10-minute-bitcoin-confirmation-barrier-a9d53a505b05#.m8d6iiz7z)

Decentralized Applications (Đapps)
----------------------------------

<https://btcmanager.com/news/blockchain-and-the-rise-of-the-prosumer/>

Altcoins
--------

### Mastercoin (now Omni)

-   <https://en.wikipedia.org/wiki/Mastercoin>
-   <https://coinmarketcap.com/currencies/omni/>
-   <http://www.coindesk.com/mastercoin-new-beginning-omni/>

Mastercoin lost a lot of credibility [through association](https://bitcointalk.org/index.php?topic=579797.0) with [the botched MaidSAFE crowdfunding disaster](http://www.forbes.com/sites/kashmirhill/2014/06/03/mastercoin-maidsafe-crowdsale/).
