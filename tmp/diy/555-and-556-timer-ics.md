---
layout: default
category: diy
title: 555 and 556 Timer ICs
permalink: p/555-and-556-timer-ics
---

Datasheets
----------

[LM555, Texas Instruments](http://www.ti.com/lit/ds/symlink/lm555.pdf)

[LM556, Texas Instruments](http://www.ti.com/lit/ds/symlink/lm556.pdf)

Oscillator Configurations
-------------------------

Dublin Institute of Technology has [a history and detailed explanation of the 555 pinout](http://www.electronics.dit.ie/staff/mtully/555%20folder/555%20timer.htm). ElectronicsTutorials has an excellent [555 oscillator tutorial](http://www.electronics-tutorials.ws/waveforms/555_oscillator.html) that describes the ways a timer oscillator can be configured. Beavis Audio Research also has [some very simple schematics](http://www.beavisaudio.com/library/555/555.htm) that illustrate these configurations, and Williamson Labs has [a cute animation](http://www.williamson-labs.com/480_555.htm).

Timer IC Pinouts
----------------

[thumb|300px](/File:555-556_pinout.png "wikilink")

**555 pinout**

    1   GND
    2   TRIG
    3   OUT
    4   RESET
    5   CTRL
    6   THR
    7   DIS
    8   V+/Vcc

**556 pinout**

    14  Vcc
    13  DIS
    12  THR
    11  CTRL
    10  RESET
    9   OUTPUT
    8   TRIG
    7   GND

**555 → 556 Correspondence**

    1 => 7
    2 => 8
    3 => 9
    4 => 10
    5 => 11
    6 => 12
    7 => 13
    8 => 14

Applications
------------

In astable mode, the 555 timer can be used as a simple pulse generator; this pulse generator can be modulated via the control pin, e.g. to construct an audio-modulated driver for a [Plasma Speaker](/Plasma_Speaker "wikilink"). It may also be used to construct a [simple overload protection circuit](http://creation-electronics.blogspot.com/2011/01/overload-protection-circuit-using-555.html).

[Category:DIY](/Category:DIY "wikilink")
