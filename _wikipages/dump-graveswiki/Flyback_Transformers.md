---
title: Flyback Transformers
permalink: /Flyback_Transformers/
---

**WARNING:** flyback transformers are capable of outputting extremely high voltages! Follow all [high voltage safety protocols](http://www.pupman.com/safety.htm) when handling!

Flyback Driver Topologies
-------------------------

[4HV.org - Uzzors2K](http://uzzors2k.4hv.org/index.php?page=flybacktransformerdrivers) - a fantastic page with lots of detail and discussion. Includes schematics for four different drivers:

1.  555 Driver - flyback mode, direct to MOSFET (IRFP450)
2.  555 Driver - flyback mode, to MOSFET (IRFP450) via [Class B](http://en.wikipedia.org/wiki/Amplifier_class#Class_B) [push-pull](http://en.wikipedia.org/wiki/Push-pull_output) output driver
3.  Mazzilli ZVS Driver - a self-oscillating zero-volt-switching push-pull driver
4.  [Multi-Purpose Inverter](http://uzzors2k.4hv.org/index.php?page=multiinverter) - 230VAC rectifier, TL494-based oscillator, and UC3710T-based gate drivers coupled to the push-pull (aka 'half bridge') MOSFETs (IRFP450) by a gate-drive transformer, with overheat and overcurrent protection

[Gauge Boson - High Voltage](http://gaugeboson.com/electronics/high_voltage.html) - an excellent description of Mazilli ZVS driver construction and operation, including links to a working simulation and some very nice point-to-point assembly.

[Pocket Magic - High Voltage Power Supplies](http://www.pocketmagic.net/2009/07/high-voltage-power-supplies/#.U5AT3HVdXCJ) - an excellent roundup of just about every driver topology that exists! Includes information on running dual ignition coils in anti-parallel, a dual flyback modification of the Mazilli ZVS that I haven't seen anyone else, a description of using voltage multipliers with AC HV sources, and links to [solid-state](http://www.pocketmagic.net/2009/12/high-frequency-solid-state-tesla-coil-hf-sstc/#.U5AVGHVdXCI) and [ZFS-based](http://www.pocketmagic.net/2009/01/tesla-coil-2/#.U5AVHXVdXCIMazilli) Tesla coil designs.

[The 4HV.org wiki page on flyback transformers](http://wiki.4hv.org/index.php/Flyback_transformer) - includes a run-down of the basic driver types, and includes a schematic of Andrinerii's modification to the Mazzilli ZVS.

[RM Cybernetics - Homemade Ignition Coil Driver](http://www.rmcybernetics.com/projects/DIY_Devices/homemade_ignition_coil_driver.htm) - a good discussion of multiple ignition coil topologies.

[Scope Boy - The IGBT Brick Driver](http://scopeboy.com/tesla/flyback.html) - a TL494-based driver for use with IGBTs; includes schematics for an audio-modulated version!

References
----------

<http://www.angelfire.com/80s/sixmhz/flyback.html>

<http://mujweb.cz/jmartis/flybacks.htm>

<http://mostlymacros2012.blogspot.com/2012/09/plasma-and-homemade-flyback-transformer.html>

<http://reibot.org/easy-high-voltage-supply/>

<http://rimstar.org/equip/30kv_pwr_supply.htm>

<http://www.sm0vpo.com/power/diy_transformers.htm>

<http://www.diyphysics.com/2012/02/09/d-i-y-250-kv-high-voltage-dc-power-supply-with-neat-trick-for-switching-polarity/>

<http://www.hvtesla.com/radartransformer.html>

<http://www.kronjaeger.com/hv/hv/src/fly/>

<http://adammunich.com/flyback-transformers/>

<http://madlabs.info/flyback.shtml>

<http://wiki.4hv.org/index.php/Flyback_transformer>

<http://www.angelfire.com/oh3/ebjoew/Flyback.html>

[Contact Performance in Relays: Contact Protection](http://www.leachintl2.com/english/english2/vol6/properties/00049.html) - an excellent tutorial on protecting switches from flyback while driving highly inductive loads. Very relevant to protecting MOSFETS in flyback drivers!