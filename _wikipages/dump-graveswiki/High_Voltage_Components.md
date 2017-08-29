---
title: High Voltage Components
permalink: p/high-voltage-components
layout: wikipage
category: diy
---

To build high voltage equipment, you must acquire some specialty semiconductor components purpose-built to survive the these operating conditions. This can be tricky and expensive, but don't give up! This page will help you track down the components you need.

HV Diodes and Rectifiers
------------------------

High voltage diodes are necessary for [rectifying the HV input to a Tesla coil's LC tank](http://uzzors2k.4hv.org/index.php?page=tabletopteslacoil) and for constructing Greinacher multipliers (aka [Cockcroft-Walton Generator](http://en.wikipedia.org/wiki/Cockcroft%E2%80%93Walton_generator)). If the HV input is high-frequency, 'fast recovery' (&lt;100ns) diodes should be used; for low-frequency HV (for instance, the 50-60 Hz output from many neon sign transformers), a normal slow recovery diode is fine.

In the past, the Philips BY8406 (25mA @ 10kV) was a popular solution. This diode no longer appears to be available, but semiconductor cross-reference documents assembled by [Matthieu Benoit](http://matthieu.benoit.free.fr/cross/competitive/philips/SemiCon%20equivalent%20Ph.pdf) and [Voltage Multipliers Inc](http://www.voltagemultipliers.com/CrossReferencedDiodesPhilips/PhilipsCrossRef.htm) suggest that there are several alternatives:

-   Sanken SHV-06
-   Diotec DD600
-   VMI [1N6535](http://www.voltagemultipliers.com/pdf/SF07_1N6513-1N6535.pdf)

[1N6535](http://www.voltagemultipliers.com/html/selection_guide_hv_diodes.html) 10KV 25mA 70ns $4.63

From [Information Unlimited](http://www.amazing1.com/capacitors.html):

| Model     | Voltage | Current | Response | Price  |
|-----------|---------|---------|----------|--------|
| VG6       | 6kv     | 5mA     | 100ns    | $1.95  |
| VG12      | 12kv    | 10mA    | 100ns    | $1.95  |
| VG16      | 16kv    | 5mA     | 100ns    | $2.95  |
| VG30      | 30kv    | 10mA    | 100ns    | $4.95  |
| VG30KV20  | 30kv    | 20mA    | 100ns    | $10.50 |
| VG15KV60  | 15kV    | 60mA    | slow     | $12.95 |
| VG15KV200 | 15kV    | 200mA   | slow     | $12.95 |

High Voltage Transformers
-------------------------

### Flyback Transformers

[POWERLABS High-Voltage Solid-State Flyback Driver](http://www.scribd.com/doc/217714950/POWERLABS-High-Voltage-Solid-State-Flyback-Driver)

> The best flybacks come from old TV's or monitors, specially the larger ones, and have a disk shaped secondary.Black and white TV flybacks tend to have a higher internal capacitance and higher step-up ratio, whilst monitor flybacks are pretty much useless, as far as the modern ones are concerned. If your flyback was used in association with a cascade, you can expect to obtain no more than perhaps 12kV from it (with 12V input). However, if it was free-standing, over 30kV may be obtainable (with higher input voltages). Nominal output current is 1-2mA, and arcing current can be as high as 10mA and above (mine can melt a steel sewing needle!).
>
> As you can see, it has a rather disk-shaped secondary: This is very important as it usually indicates a large number of secondary turns, and a proportionally high output voltage... The primary coil is wound on a plastic form that sits opposite to the secondary. The rectangular piece of aluminium holds the flyback in place and also serves as a heat sink (as it contains "thermal compound" between it and the ferrite core).he secondary is nearly 10cm (4") in diameter, and 5cm (2") tall, and the core has 1.5cm cross section,and is a square some 10cm on each side. This is by far the best type of flyback to use in high performance circuits. My particular model is a "TDK H1322Q". It has never been used before (I bought the last two an appliance repair shop held as replacement parts. It only cost me 5 dollars!), but is a real antique, and VERY rare to find... If you can get your hands in such a beauty, I'm highly interested. Do not hesitate to e-mail me! The person who sold it to me said it was used in those old black and white valveVs from the 70's, supposedly a "Phillips" or "Philco" model... I'm not 100% sure, but the last valve TV Iook apart had a huge screen, and a very small flyback, so a large old TV is no guarantee of a largelyback. Also note that if you remove your flyback from an old TV it may well have it's secondary winding burned out... Flybacks are built tough, but they are high voltage parts, and as such they tend to have a limited useful life. If it is the primary that is burned out, than it may simply be removed as you will wind anew one either way.

[DIY HV Ion Generator](http://fear-of-lightning.wonderhowto.com/how-to/high-voltage-happiness-make-negative-ion-generator-0133359/)

> Depending on the flyback, the output should be DC. It's VERY rare you'll find an un-rectified flyback unless you've used a very old TV. The AC flybacks are extremely useful and are worth their weight in gold, but that's another story.

[Flyback Transformers](http://mujweb.cz/jmartis/flybacks.htm)

> Type 1 is the older AC unrectified type. This one isn't usually good for anything over 30kV, because it will flash over soon (and also because it has usually low number of turns on its secondary winding and thus it is difficult to get high voltages out of it). However it is often suitable for higher power outputs than the other types. Found in old TVs.

[Flyback Transformer Drivers](http://uzzors2k.4hv.org/index.php?page=flybacktransformerdrivers)

> Contrary to the 555 drivers this driver provides actual AC to the primary, and due to DC flybacks being half-wave rectified you'll likely have problems with saturation regardless. I've run DC flybacks offline several times, but they have all failed eventually, and they cause the driver to heat up. Unrectified AC flybacks are much more suitable for this driver, and cause very little heating of the mosfets. See my article on making HV transformers for details: <http://uzzors2k.4hv.org/index.php?page=hvxfrmrwinding>

Page Details
------------

This page is synchronized with the [BC Wiki page on High Voltage Components](http://wiki.brandoncurtis.com/w/High_Voltage_Components).
