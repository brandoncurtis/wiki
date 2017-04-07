---
layout: default
category: software
permalink: p/arduino
featured: true
title: Arduino Hacking
description: Getting the most out of the Arduino hardware prototyping system
author: brandoncurtis
---

The Arduino does an excellent job of abstracting away the implementation details of a microcontroller and allowing the user to think about it as a collection of easy-to-use high-level functions.

### Compile and Upload from the CLI

You can upload code to an Arduino using the command-line interface:

`arduino --upload --port /dev/arduino --board arduino:avr:uno filename.ino


### Programmatic Resets

Lots of discussion in the [Disabling AutoReset on Serial Connection](http://playground.arduino.cc/Main/DisablingAutoResetOnSerialConnection) page on the Arduino site.

Disable hangup-on-close in Linux: `stty -F /dev/arduino-uno -hupcl`

After setting this, reading the data printed over the serial device will not cause the Arduino to reset: `cat /dev/arduino-uno`

To make it reset-on-connection again, just run: `stty -F /dev/arduino-uno hupcl`

Now that you know what controls the Arduino reset, you can even reset it yourself from Python:

    >>> import serial
    >>> from time import sleep
    >>> arduino = serial.Serial('/dev/arduino_uno',bytesize=serial.EIGHTBITS,
    ...                      parity=serial.PARITY_NONE,
    ...                      stopbits=serial.STOPBITS_ONE,
    ...                      timeout=1,
    ...                      xonxoff=0,
    ...                      rtscts=0
    ...                      )
    >>> arduino.setDTR(False); sleep(1); arduino.flushInput(); arduino.setDTR(True)

More notes on these ideas:

    Wait on Arduino auto-reset using pySerial
    https://stackoverflow.com/questions/21073086/wait-on-arduino-auto-reset-using-pyserial

    Reset Arduino from Python!

    Linux: serial port, Arduino reset, avrdude
    http://forum.arduino.cc/index.php?topic=39468.0

    DisablingAutoResetOnSerialConnection
    http://playground.arduino.cc/Main/DisablingAutoResetOnSerialConnection


    http://www.codeproject.com/Articles/1012319/Arduino-Software-Reset
    http://www.theengineeringprojects.com/2015/11/reset-arduino-programmatically.html
    http://www.xappsoftware.com/wordpress/2013/06/24/three-ways-to-reset-an-arduino-board-by-code/
    https://arduino.stackexchange.com/questions/1477/reset-an-arduino-uno-by-an-command-software
    Reset command
    http://forum.arduino.cc/index.php?topic=12874.0

    http://playground.arduino.cc/Main/ArduinoReset

    http://www.instructables.com/id/two-ways-to-reset-arduino-in-software/
