---
title: Plasma Speaker
permalink: p/plasma-speaker
layout: default
category: diy
---

Basic Design
------------

Video: <https://www.youtube.com/watch?v=o_1lPekb2lY>

The basic design was inspired by [this schematic on Kaizer Power Electronics](http://kaizerpowerelectronics.dk/high-voltage/555-audio-modulated-flyback/), which discusses MOSFET selection and gate protection.

In this setup, a [555 timer IC –based astable multivibrator oscillator circuit](/555_and_556_Timer_ICs "wikilink") (powered independently with a 5V 2A wall adapter) switches a 12V 1.2A power supply via a silicon diffused power transistor into a television flyback transformer. The high-voltage transformer secondary is allowed to arc across a spark gap made from a screw and a piece of copper magnet wire.

The frequency and duty cycle of the oscillator circuit is tuned with two 0-10kΩ potentiometers and audio-modulated by tying the 555's control voltage (Pin 5; Pin 11 on the 556) to an audio input in series with a 100nF ceramic capacitor.

The resulting hot plasma arc does an excellent job of reproducing audio above 1kHz. Two Door Cinema Club's "Something Good Can Work (The Twelves Remix)" is quite recognizable. With a larger power supply, I should be able to pull much larger, more stable arcs and improve the sound quality.

Virtually all of the parts were harvested from electronics salvaged from the Bay Area streets. Don't just throw out old electronics — donate them to your neighborhood aspiring mad scientist!

The Audio Input
---------------

The audio input will be attached to the control pin of the timer IC; this is Pin 5 on the 555 and Pin 3/11 on the 556.

To eliminate any chance of feeding radio-frequency nasties back into your audio source, capacitively couple your audio source to the control pin by placing a 100nF capacitor in series as demonstrated in [this schematic by Bogin Jr](http://boginjr.com/electronics/hv/flyback-driver-2/).

Advanced Designs
----------------

An [alternative design](http://adammunich.com/plasma-speaker-1/) uses the 3525 pulse-width modulation IC but is otherwise very similar; [another uses the TL494 waveform generator](http://jordancolburn.com/2011/05/17/plasma-speaker/) and two IRF740 MOSFETs in series, and speculates on how a 'plasma tweeter' might be integrated with a conventional speaker to improve frequency range.

More [advanced versions use a gate drive transformer and two MOSFETs in a half-bridge topology](http://adammunich.com/plasma-speaker-2/) to reduce the strain on the MOSFETs and keep things cool.

### ZVS-Based Drivers

Videos:

-   [Plasma Speaker - Singing Arc: HV ZVS Flyback driver project](https://www.youtube.com/watch?v=_9ml_Fd8uIY)
-   [Audio Modulated ZVS driver (Plasma Speaker) Rev 2](https://www.youtube.com/watch?v=fmAAndVCYMk)

"ZVS through Class A Amplifier"

[Singing Arc Plasma Speaker project - revision 2.0!](http://www.instructables.com/id/Singing-Arc-Plasma-Speaker-project-revision-20/?ALLSTEPS)

> "After mucking around with a TIP3055 and some other smaller BJT transistors, I made myself a decent audio amplifier that should be able to modulate a L2 coil around the same ferrite core as the L1 in my previous schematic."

[Category:DIY](/Category:DIY "wikilink")
