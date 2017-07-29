---
title: Arduino
permalink: p/arduino
layout: default
category: diy
---

__FORCETOC__

Procurement
-----------

Arduino Uno - R3 <https://www.sparkfun.com/products/11021> $24.95

Arduino Uno - R3 SMD <https://www.sparkfun.com/products/11224> $29.95

IEIK UNO R3 Board ATmega328P with USB Cable for Arduino <http://www.amazon.com/gp/product/B00P2FX9WY/> $10.49

Arduino Compatible Uno R3 Rev3 Development Board <https://www.fasttech.com/product/1001700-arduino-compatible-uno-r3-rev3-development-board> $7.24

Arduino UNO R3 development board microcontroller /w USB cable 328P DCCduino <http://www.newegg.com/Product/Product.aspx?Item=9SIA7BF2K19064> $11.96

Arduino Interrupts
------------------

-   <http://playground.arduino.cc/Code/Interrupts>
-   <https://www.arduino.cc/en/Reference/AttachInterrupt>
-   <https://learn.adafruit.com/multi-tasking-the-arduino-part-2/external-interrupts>
-   <http://www.engblaze.com/we-interrupt-this-program-to-bring-you-a-tutorial-on-arduino-interrupts/>
-   <https://www.sparkfun.com/tutorials/326>
-   <http://makezine.com/2012/01/25/how-to-arduino-interrupts/>
-   <http://www.bristolwatch.com/arduino/arduino_irq.htm>

Arduino-Compatible Hardware
---------------------------

### LED Displays

5V MAX7219 8-Digit Red LED Display Module 7 Segment Digital Tube For Arduino MCU <http://www.amazon.com/dp/B00IHQ7STK/>

Adafruit 0.56" 4-digit 7-segment Display W/i2c Backpack - Green <http://www.amazon.com/dp/B00GJRQUTS/>

Anycubic MAX7219 CWG 8-Digit Digital Display Control Module 8-Digit 7 Segment Digital LED Display Tube for Arduino <http://www.amazon.com/dp/B014P8S3PG>

Arduino Software IDE
--------------------

### Build From Source for Ubuntu

-   <https://github.com/arduino/Arduino>
-   <https://github.com/arduino/Arduino/wiki/Building-Arduino>

<!-- -->

    sudo apt-get install git make gcc ant openjdk-8-jdk
    git clone git://github.com/arduino/Arduino.git
    cd /path/to/arduino/build
    ant dist
    ant run
    sudo mkdir /opt/arduino
    sudo chown brandon: /opt/arduino
    cp linux/arduino-1.6.10-linux64.tar.xz /opt/arduino/
    cd /opt/arduino/
    tar xvJf arduino-1.6.10-linux64.tar.xz
    cd arduino-1.6.10/
    ./install.sh

    # to update later:
    cd /path/to/arduino
    git pull
    ant clean build start

### Packing for Debian/Ubuntu

Looks like [licensing issues are keeping the newer Arduino IDEs from making it into the Debian/Ubuntu repos](https://github.com/arduino/Arduino/pull/2703).

-   <https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=780706>
-   <https://packages.debian.org/experimental/arduino>

<!-- -->

    From: Scott Howard <showard314@gmail.com>
    To: 780706@bugs.debian.org
    Subject: Update re: arduino 1.6+
    Date: Fri, 8 Apr 2016 17:18:08 -0400

    [Message part 1 (text/plain, inline)]

    The update is there is no update. The Debian git repository is still ready
    to go,. I don't have time to work on it that much at the moment (either on
    following up with licensing or packaging), so if anyone is interested in
    helping out in any way (including co-maintaining or adopting the package),
    please let me know.
    ~Scott

Scott Howard looks like a really cool person:

-   <https://engineering.nd.edu/profiles/hscott>
-   <https://wiki.ubuntu.com/ScottHoward/ContributingDeveloperApplication>
-   <https://lists.debian.org/debian-newmaint/2010/12/msg00023.html>
-   <https://www.linkedin.com/in/scott-howard-688a3b30>

Here are some Debian build instructions that are current as of 1.6.7: <https://bugs.launchpad.net/ubuntu/+source/arduino/+bug/1425677/comments/10>

"There are a few problems with getting this packaged as v1.6.6 requires Java 8. I almost got a complete build of the package with arduino-1.6.5-r3 from arduino.cc and Scott Howard's debian/ folder from his repository. Anything later than that version requires Java 8. I'm still using Trusty and won't be upgrading from that until the next LTS is released."

Looks like there is some older Arduino source here, and it contains a debian folder with build instructions: <http://anonscm.debian.org/cgit/collab-maint/arduino.git>

This repo DOES build successfully in Ubuntu 16.04; though it's labeled '1.5' or '1.6' in the repo, it generates a Debian installer version 1.0.5.

References related to the version numbering:

-   <https://www.arduino.cc/en/Main/OldSoftwareReleases>
-   <https://www.arduino.cc/en/Main/Software>
-   <https://www.arduino.cc/en/Main/ReleaseNotes>
-   <http://forum.arduino.cc/index.php?topic=274537.0>
-   <http://arduino.stackexchange.com/questions/4350/now-at-ide-1-0-5-should-i-upgrade-to-1-0-6-or-1-5-7-beta-for-pro-mini-and-atmeg>
-   <http://arduino.stackexchange.com/questions/9511/what-are-the-differences-between-the-1-0-x-and-1-6-x-ides>
-   <https://groups.google.com/a/arduino.cc/forum/#!searchin/developers/ubuntu/developers/rlbxoXmV9Q8/PTAWW0FGEqQJ>
-   <https://groups.google.com/a/arduino.cc/forum/#!searchin/developers/ubuntu/developers/P2El6mR7onQ/J_s4BLAeVBIJ>
-   <https://groups.google.com/a/arduino.cc/forum/#!searchin/developers/ubuntu/developers/rlbxoXmV9Q8/PTAWW0FGEqQJ>

AVR Programming
---------------

Procurement:

-   <http://www.atmel.com/products/microcontrollers/avr/xplained.aspx>
-   <http://www.atmel.com/tools/MEGA328P-XMINI.aspx>
-   <http://www.atmel.com/tools/MEGA328PB-XMINI.aspx>
-   <http://www.atmel.com/Images/Atmel-42559-Differences-between-ATmega328P-and-ATmega328PB_Application%20Note_AT15007.pdf>
-   [AVR Programming: Learning to Write Software for Hardware 1st Edition](http://www.amazon.com/AVR-Programming-Learning-Software-Hardware/dp/1449355781/)

Setting up development tools:

-   [Lady Ada: Step-by-step how to install AVR dev tools](http://www.ladyada.net/learn/avr/setup-unix.html)
-   [AVR Microcontrollers in Linux HOWTO](http://www.tldp.org/HOWTO/Avr-Microcontrollers-in-Linux-Howto/x207.html)
-   [Setting up AVR development environment in Ubuntu](https://stringofthoughts.wordpress.com/2009/11/06/setting-up-avr-development-environment-in-ubuntu/)
-   [Ubuntu Forums: Atmel AVR programming](http://ubuntuforums.org/showthread.php?t=2034854)
-   [AVR Programming in Ubuntu](https://sites.google.com/site/abhijit86kavr/home/avr-programming-in-ubuntu)
-   [Beginning Atmel AVR Development in Linux using AVR-Eclipse, AVR-GCC and AVRDUDE](http://www.timteatro.net/2012/03/22/beginning-atmel-avr-development-in-linux-using-avr-eclipse-avr-gcc-and-avrdude/)
-   [AVR - How to program an AVR chip in Linux](http://electronics.stackexchange.com/questions/66145/avr-how-to-program-an-avr-chip-in-linux/66163)
-   [The AVR GCC Toolchain](http://avr-eclipse.sourceforge.net/wiki/index.php/The_AVR_GCC_Toolchain)
-   [AVR Programming in Linux](http://www.swharden.com/blog/2013-01-06-avr-programming-in-linux/)
-   [How to Install The Latest AVRDude 6.1 in Ubuntu 14.04](http://ubuntuhandbook.org/index.php/2014/09/install-avrdude-6-1-ubuntu-1404/)
-   [HowTo Setup Eclipse for AVR software development (for ubuntu)](https://blogs.fe.up.pt/fbnsantos/2010/12/16/howto-setup-eclipse-for-avr-software-development/)
-   \[<http://manpages.ubuntu.com/manpages/precise/man1/avrp.1.html>
-   [avrp - Atmel AVR programming software to use with Atmel's serial-port programmers](http://manpages.ubuntu.com/manpages/precise/man1/avrp.1.html)
-   [Steps for running C-program for AVR microcontroller on Linux](https://www.cse.iitb.ac.in/~erts/html_pages/Resources/FirebirdLinux/Programming%20AVR%20from%20Linux.pdf)
-   [AVR PROGRAMMING 01: INTRODUCTION](http://hackaday.com/2010/10/23/avr-programming-introduction/)

Get Involved
------------

Arduino community fora:

-   [Arduino repo on Github](https://github.com/arduino/arduino)
-   [Arduino developers list](https://groups.google.com/a/arduino.cc/forum/#!forum/developers)
-   [Arduino teachers list](https://groups.google.com/a/arduino.cc/forum/#!forum/teachers)
-   [Arduino user forum](http://forum.arduino.cc/)

Variants and Alternatives
-------------------------

### STMduino

    https://en.wikipedia.org/wiki/STM32
    "STM32 is a family of 32-bit microcontroller integrated circuits by STMicroelectronics."

    http://www.stm32duino.com/
    https://github.com/rogerclarkmelbourne/Arduino_STM32
    http://arduino-for-beginners.blogspot.com/search/label/STM32duino
    http://www.rogerclark.net/arduino-stm32-usb-serial-and-dfu/
    https://c9.io/serasidis/stm32duino
    http://www.jyetech.com/forum/viewtopic.php?f=18&t=658
    http://analoglamb.com/shop/stm32duino
    http://www.davidpilling.net/wiki/index.php/STM32
    http://xtl.kapsi.fi/blog.2015-07-14.STM32duino_setup.html

[Category:DIY](/Category:DIY "wikilink")
