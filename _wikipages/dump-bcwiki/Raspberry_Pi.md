---
layout: default
title: Raspberry Pi
permalink: p/raspberry-pi
category: diy
---

Models and Performance
----------------------

[Understanding the system/gpu RAM split](https://raspberrypi.stackexchange.com/questions/56266/raspberry-pi-3-has-less-than-1gb-memory-available-at-os-level)

Raspberry Pi Setup
------------------

-   <http://www.jameco.com/1/1/59033-raspi2-bundle-raspberry-pi-2-model-b-starter-accessory-bundle.html>
-   <https://ubuntu-mate.org/raspberry-pi/>
-   <https://www.linux.com/learn/tutorials/818062-getting-started-with-raspberry-pi-2-install-arch-linux>

### Flash-Friendly File System (f2fs)

"Added f2fs support to the build script. Pre-built images available for download use ext4 because f2fs file systems can not be resized at present."

-   <http://askubuntu.com/questions/458211/how-to-format-my-pendrive-with-f2fs-filsystem-using-gparted>
-   <http://ubuntuforums.org/showthread.php?t=2241328>
-   <http://askubuntu.com/questions/267793/how-to-make-use-of-f2fs>
-   <http://askubuntu.com/questions/452914/installing-ubuntu-14-04-on-a-f2fs-partition>
-   <https://en.wikipedia.org/wiki/F2FS>
-   <https://www.reddit.com/r/Nexus5/comments/2qhzxk/eli5_what_exactly_is_f2fs_and_how_is_it_different/>
-   <http://www.xda-developers.com/f2fs-put-to-the-test-against-ext4/>

### Memory Card Selection

-   <https://en.wikipedia.org/wiki/Secure_Digital>
-   <https://www.sdcard.org/developers/overview/speed_class/>
-   <https://ubuntu-mate.org/raspberry-pi/>

"We have done what we can to optimise the build for the Raspberry Pi 2 and one can comfortably use applications such as LibreOffice, which in fact is a joy to use :-) But the microSDHC I/O throughput is a bottleneck so we recommend that you use a Class 6 or Class 10 microSDHC card. If you build the image yourself we recommend you use the f2fs filesystem."

### Creating Swap with dphys-swapfile

On Ubuntu, install with \`sudo apt install dphys-swapfile\`.

The configuration file is in \`/etc/dphys-swapfile\`. Set swap location with \`CONF_SWAPFILE=/your/location\` and set size in megabytes with \`CONF_SWAPSIZE=100\`.

Use \`systemd\` to control it:

-   \`sudo systemctl status dphys-swapfile\`
-   \`sudo systemctl enable dphys-swapfile\`
-   \`sudo systemctl start dphys-swapfile\`
-   \`sudo systemctl stop dphys-swapfile\`
-   \`sudo dphys-swapfile uninstall\`

References:

-   <http://neil.franklin.ch/Projects/dphys-swapfile/>
-   <http://manpages.ubuntu.com/manpages/trusty/man8/dphys-swapfile.8.html>
-   <http://raspberrypi.stackexchange.com/questions/70/how-to-set-up-swap-space>

Some people will tell you that making a swapfile on an SD card is a recipe for disaster; others will tell you that swap thrashing is not a realistic concern. I keep my swapfile on a spinning disk connected to the Raspberry Pi.

Peripherals
-----------

[Non-Contact Temperature Measurement](/Non-Contact_Temperature_Measurement "wikilink")

### Pinout

-   <http://www.element14.com/community/thread/41562/l/the-correct-ribbon-cable-for-raspberry-pi-2-model-b?displayFullThread=true>
-   <http://hackaday.com/2012/06/17/using-the-gpio-pins-on-a-raspberry-pi/>
-   <http://raspi.tv/wp-content/uploads/2014/07/Raspberry-Pi-GPIO-pinouts.png>
-   <https://learn.adafruit.com/introducing-the-raspberry-pi-model-b-plus-plus-differences-vs-model-b/gpio-port>

Configuration
-------------

### Serial Interfaces (SPI and I2C)

    https://www.raspberrypi.org/forums/viewtopic.php?f=44&t=121440

    https://www.raspberrypi.org/forums/viewtopic.php?f=66&t=11617
    You need to load the 'spidev' module to get userspace spi device access, in the same way the i2c-dev module provides userspace i2c access.
    Try "modprobe spidev".

    how to detect spi devices?

### Scientific Computing

    pip install matplotlib memory error
    http://raspberrypi.stackexchange.com/questions/34644/pip-exception-while-installing-matplotlib-on-raspberry-pi
    pip install --no-cache-dir matplotlib

    http://stackoverflow.com/questions/20533426/ubuntu-running-pip-install-gives-error-the-following-required-packages-can-no
    apt-get install libfreetype6-dev libpng12-dev
    pip install matplotlib

Bugs
----

### Wireless Sequencing Error

[RPi3 wifi sequence error](https://www.raspberrypi.org/forums/viewtopic.php?t=141684&p=937731)

problem: \`brcmfmac: brcmf_sdio_hdparse: seq 194: sequence number error\` in console when receiving wifi packets

### Missing Console Cursor

[Ubuntu Mate for Raspberry Pi](https://ubuntu-mate.org/raspberry-pi/)

    "We created a simple utility called graphical to disable/enable the MATE desktop environment for easily creating a headless “server”. Executing graphical disable will present a console login on the next boot, with no X11 or associated services running. If you want to get the full Ubuntu MATE desktop back, run graphical enable and reboot."

Problem: can't see cursor position in terminal when rebooting after \`graphical disable\`

Programming
-----------

### Controlling General-Purpose I/O with Python

    Raspberry gPIo
    https://learn.sparkfun.com/tutorials/raspberry-gpio

    "Driving the Raspberry Pi’s I/O lines requires a bit of programming. Programming in what language? Take your pick! A quick glance at the Raspberry Pi GPIO examples shows that there are dozens of programming-language-choices. We’ve pared that list down, and ended up with two really solid, easy tools for driving I/O: Python and C (using the WiringPi library)."

    Pins 2,4 - 5VDC
    Pins 6,9,14,20,25,30,34,39 - Ground

    Python module: RPi.GPIO
    https://sourceforge.net/projects/raspberry-gpio-python/

    "Note that this module is unsuitable for real-time or timing critical applications. This is because you can not predict when Python will be busy garbage collecting. It also runs under the Linux kernel which is not suitable for real time applications - it is multitasking O/S and another process may be given priority over the CPU, causing jitter in your program. If you are after true real-time performance and predictability, buy yourself an Arduino! (see http://www.arduino.cc  )

    Note that the current release does not support SPI, I2C, 1-wire or serial functionality on the RPi yet. This is planned for the near future - watch this space!"

    https://pypi.python.org/pypi/RPi.GPIO
    RPi.GPIO 0.6.2

    pip install rpi.gpio
    Collecting rpi.gpio
      Downloading RPi.GPIO-0.6.2.tar.gz

    import RPi.GPIO as GPIO
    GPIO.setmode(GPIO.BOARD)
    GPIO.setup(18, GPIO.OUT)
    GPIO.output(18, GPIO.HIGH)
    pwm = GPIO.PWM(18, 1000)
    pwm.start(50)
    if GPIO.input(17):
        print("Pin 11 is HIGH")
    else:
        print("Pin 11 is LOW")
    GPIO.setup(17, GPIO.IN, pull_up_down=GPIO.PUD_UP)

[Category:DIY](/Category:DIY "wikilink")
