---
title: Packaging Software for Ubuntu
permalink: /Packaging_Software_for_Ubuntu/
---

    How to package newer version of Arduino for Ubuntu?
        http://packaging.ubuntu.com/html/packaging-new-software.html
        https://wiki.debian.org/Packaging/Intro?action=show&redirect=IntroDebianPackaging
        Must set DEBEMAIL and DEBFULLNAME
        Sudo apt-get install ubuntu-dev-tools
        http://ubuntuforums.org/showthread.php?t=886307
        “you can only upload source packages, launchpad will then build deb files for every supported architecture for you.”
        http://packages.ubuntu.com/precise/
        https://www.debian.org/doc/debian-policy/ch-controlfields.html

    http://packaging.ubuntu.com/html/packaging-new-software.html
    http://packaging.ubuntu.com/html/getting-set-up.html
    https://launchpad.net/~brandoncurtis

Packaging with Apache Ant
-------------------------

I have not been able to successful compile Java software for Debian using Apache Ant, but my notes so far are below for the attempts to come.

My plan is to read the [Apache Ant how-to](https://ant.apache.org/manual/tutorial-HelloWorldWithAnt.html), explore the source of the very old [Arduino v1.0.5](https://launchpad.net/ubuntu/xenial/+source/arduino) in the repositories and look for clues to how to package for Debian with Ant. Failing that, I will ask for help on the Arduino developer mailing list.

[nekoconeko.nl - Java and Debian Packaging](https://blog.nekoconeko.nl/blog/2013/08/28/java_and_debian_packaging.html)

    http://packaging.ubuntu.com/html/getting-set-up.html

    this is what we currently have, all the way back at 1.0.5:
    https://launchpad.net/ubuntu/xenial/+source/arduino

    1) install and configure software:
    sudo apt-get install packaging-dev
    pbuilder-dist xenial create

    nano ~/.bashrc
    export DEBFULLNAME="Bob Dobbs"
    export DEBEMAIL="subgenius@example.com"
    source ~/.bashrc


    2) create gpg and ssh keys

    (I just copied the .gnugp folder from my old install!)


    3) set up to work with Launchpad

    https://launchpad.net/~brandoncurtis
    https://launchpad.net/~/+editpgpkeys
    https://launchpad.net/~/+editsshkeys

    bzr whoami "Brandon Curtis <brandon.curtis@gmail.com>"
    bzr launchpad-login brandoncurtis

    ----
    http://packaging.ubuntu.com/html/packaging-new-software.html

    work through this example to package a HELLO WORLD app
    and upload it to a PPA on Launchpad.
    ----
    https://blog.nekoconeko.nl/blog/2013/08/28/java_and_debian_packaging.html

    this (hopefully) contains the information necessary to create PPAs
    for Java software packaged with Ant.

    sudo apt-get install javahelper
    ----
    details on the different sections in the control file:
    https://www.debian.org/doc/debian-policy/ch-controlfields.html

    list of potential sections your package could fall under:
    http://packages.ubuntu.com/xenial/

    get a package's dependencies with `apt-cache depends arduino`

    arduino
     |Depends: default-jre
      Depends: <java6-runtime>
        default-jre
        openjdk-8-jre
        openjdk-9-jre
      Depends: libjna-java
      Depends: librxtx-java
      Depends: arduino-core
      Recommends: extra-xdg-menus
      Recommends: policykit-1
        policykit-1:i386

    (control still needs work)
    ----
    for rules, maybe try something like this?

    #!/usr/bin/make -f
    # -*- makefile -*-

    # Uncomment this to turn on verbose mode.
    #export DH_VERBOSE=1

    JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64

    %:
        dh $@  --with javahelper

    override_dh_auto_build:
        dh_auto_build -- dist

    override_dh_install:
        dh_auto_build -- run
        dh_install
    ----
    perform the build:
    dpkg-buildpackage -A -us -uc
    ----
    More references:
     - https://wiki.debian.org/Java/Packaging
     - http://foolcontrol.org/?p=1685
     - http://ask.debian.net/questions/packaging-java-applications-in-debian