---
title: Apache
permalink: p/apache
layout: default
category: software
---

Apache 2.2 in Ubuntu 14.04
--------------------------

    deb http://archive.ubuntu.com/ubuntu precise main restricted universe
    deb http://archive.ubuntu.com/ubuntu precise-updates main restricted universe
    deb http://security.ubuntu.com/ubuntu precise-security main restricted universe multiverse

    sudo apt-get update
    sudo apt-get autoremove

    sudo apt-get install apache2-mpm-prefork=2.2.22-1ubuntu1.10 \
      apache2-prefork-dev=2.2.22-1ubuntu1.10 \
      apache2.2-bin=2.2.22-1ubuntu1.10 \
      apache2.2-common=2.2.22-1ubuntu1.10

    http://askubuntu.com/questions/64454/how-do-i-enable-the-mod-rewrite-apache-module-for-ubuntu-11-04
    sudo a2enmod rewrite

    https://wiki.apache.org/httpd/CommonMisconfigurations
    ports.conf
        comment out 'NameVirtualHost' and 'Listen'

    https://www.digitalocean.com/community/tutorials/how-to-configure-the-apache-web-server-on-an-ubuntu-or-debian-vps
    sudo a2dissite default
    (I believe this was also listening on port 80!)

    http://stackoverflow.com/questions/15850465/invalid-command-proxyrequests-when-setting-up-jenkins
    a2enmod proxy

    https://www.digitalocean.com/community/tutorials/installing-mod_wsgi-on-ubuntu-12-04
    sudo aptitude install libapache2-mod-wsgi

    WSGIDaemonProcess

    ERROR: Module wsgi does not exist!
    http://askubuntu.com/questions/25374/how-do-you-install-mod-wsgi
    sudo nano /etc/apache2/mods-available/wsgi.load
    LoadModule wsgi_module /usr/lib/apache2/modules/mod_wsgi.so
    sudo a2enmod wsgi
    sudo service apache2 restart

    need to install libapache2-mod-php5
    http://serverfault.com/questions/527631/libapache2-mod-php5-uninstalled-after-update-impossible-to-put-back
    http://packages.ubuntu.com/precise/libapache2-mod-php5

    sudo apt-get install libapache2-mod-php5=5.3.10-1ubuntu3.21
    libapache2-mod-php5 : Depends: php5-common (= 5.3.10-1ubuntu3.21) but 5.5.9+dfsg-1ubuntu4.14 is to be installed

    sudo apt-get install php5-common=5.3.10-1ubuntu3.21

    The following packages will be REMOVED:
      php-auth-sasl php-mail php-net-smtp php-net-socket php-pear php5 php5-cli
      php5-dbg php5-dev php5-fpm php5-gd php5-json php5-mcrypt php5-mysql
      php5-readline pkg-php-tools

    PHP Version => 5.5.9-1ubuntu4.14

    http://packages.ubuntu.com/precise/php/
    php5 (5.3.10-1ubuntu3.21) [security]
    -----
    The following actions will resolve these dependencies:

          Remove the following packages:
    1)      php5-fpm
    2)      php5-json
    3)      php5-mcrypt
    4)      php5-readline

          Install the following packages:
    5)      libdb5.1 [5.1.29-7ubuntu1 (now, trusty)]
    6)      libgd2-xpm [2.0.36~rc1~dfsg-6ubuntu2 (now, precise)]
    7)      libt1-5 [5.1.2-3.6ubuntu1 (now, trusty)]
    8)      php5-cgi [5.3.10-1ubuntu3.21 (precise-security, precise-updates)]

          Downgrade the following packages:
    9)      php-pear [5.5.9+dfsg-1ubuntu4.14 (now, trusty-security, trusty-updates) -> 5.3.10-1
    10)     php5 [5.5.9+dfsg-1ubuntu4.14 (now, trusty-security, trusty-updates) -> 5.3.10-1ubun
    11)     php5-cli [5.5.9+dfsg-1ubuntu4.14 (now, trusty-security, trusty-updates) -> 5.3.10-1
    12)     php5-dbg [5.5.9+dfsg-1ubuntu4.14 (now, trusty-security, trusty-updates) -> 5.3.10-1
    13)     php5-dev [5.5.9+dfsg-1ubuntu4.14 (now, trusty-security, trusty-updates) -> 5.3.10-1
    14)     php5-gd [5.5.9+dfsg-1ubuntu4.14 (now, trusty-security, trusty-updates) -> 5.3.10-1u
    15)     php5-mysql [5.5.9+dfsg-1ubuntu4.14 (now, trusty-security, trusty-updates) -> 5.3.10

          Leave the following dependencies unresolved:
    16)     php5-cli recommends php5-readline

    Accept this solution? [Y/n/q/?]
    IT WORKED.
    ----
    sudo a2enmod php5

    missing php5.load
    /etc/php5/apache2/

    LoadModule wsgi_module /usr/lib/apache2/modules/mod_wsgi.so
    LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
    ----
