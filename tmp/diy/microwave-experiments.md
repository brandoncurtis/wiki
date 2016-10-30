---
layout: default
category: diy
title: Microwave Experiments
permalink: p/microwave-experiments
---

Microwave Fundamentals
----------------------

Microwaves will cause [microwave burns](http://en.wikipedia.org/wiki/Microwave_burn) by capacitive coupling and dielectric heating. At the 2.45GHz frequency used by commercial microwave ovens, water-rich muscle tissues are preferentially heated and damage to deep tissues may occur before the pain threshold is reached.

-   [Notes on the Troubleshooting and Repair of Microwave Ovens](http://www.repairfaq.org/REPAIR/F_micfaq5.html)
-   <http://www.instructables.com/id/MICROWAVE-RADIATION/>
-   [Typical Panasonic Microwave Oven Service Manual](https://www.delmarent.com/specs/panosonic/NE1257R_NE1258R_NE1757R_NE2157R.pdf)

A microwave oven is wired like this (from [ER Parts](http://www.erparts.com/)):

[File:Microwave_Wiring_Diagram.png|Wiring](File:Microwave_Wiring_Diagram.png|Wiring) Diagram [File:Microwave_Wiring_Schematic.png|Wiring](File:Microwave_Wiring_Schematic.png|Wiring) Schematic

The microwave circuit includes a Villard doubler between the transformer and the magnetron:

-   <http://en.wikipedia.org/wiki/Bridge_circuit>
-   <http://en.wikipedia.org/wiki/Topology_%28electrical_circuits%29#Bridge_topology>
-   <http://en.wikipedia.org/wiki/Clamper_%28electronics%29>
-   <http://en.wikipedia.org/wiki/Voltage_doubler>

Microwave Oven Transformers (MOTs)
----------------------------------

Problem: the microwave oven transformer core will saturate and heat up rapidly, because it's not current-limited in any way!

-   <http://wiki.4hv.org/index.php/Microwave_oven_transformer>
-   <http://www.minicircuits.com/pdfs/MPD_Transformers.pdf>
-   <http://adammunich.com/microwave-transformers/>
-   <http://www.users.on.net/~endsodds/psrewind.htm>
-   <http://www.kronjaeger.com/hv/hv/src/mot/>
-   <http://www.instructables.com/id/Taking-Apart-A-Microwave/>
-   <http://lifehacker.com/5890347/salvage-transformers-from-broken-microwaves-for-your-electronics-projects>

Microwave Experiments
---------------------

-   <http://danyk.cz/magn3_en.html>

### MOT Arcing

-   <http://www.instructables.com/id/Microwave-Transformer-fun/>

### MOT Power Supplies

-   <http://www.users.qwest.net/~ptaylor/Electronics/MOTpowersupply/MOTPSpage.html>
-   <https://arthurguy.co.uk/archive/projects/high-voltage/power-supplies/microwave-oven-transformer-power-supply>

### High-Current, Low-Voltage Metal Melters

-   <http://mad-science.wonderhowto.com/how-to/turn-microwave-oven-transformer-into-high-amperage-metal-melter-0140772/>
-   <http://www.instructables.com/id/Build-a-Microwave-Transformer-Homemade-Welder/>

### Microwave Foundry

[Melting Metals in a Domestic Microwave](https://web.archive.org/web/20120622101226/http://home.c2i.net/metaphor/mvpage.html)

### HERF Gun Designs

-   <http://www.instructables.com/id/make-a-microwave-gun-HERF-gun/>
-   <http://hacknmod.com/hack/diy-electromagnetic-herf-gun-project/>
-   <http://hackaday.com/2011/03/21/herf-gun-zaps-more-than-your-dinner/>
-   <http://forums.xkcd.com/viewtopic.php?f=18&t=28120>

### Earth-Moon-Earth

-   <http://www.dxmaps.com/discuss/oven.html>

### Microwave Plasmas

-   <http://jlnlabs.online.fr/plasma/gmrtst/>
-   <http://jlnlabs.online.fr/plasma/4wres/index.htm>
-   <http://jlnlabs.online.fr/plasma/html/oa_plasmoid.htm>
-   <http://jlnlabs.online.fr/plasma/index.htm>
-   <http://jlnlabs.online.fr/plasma/html/oa_plsm4.htm>
-   <http://jlnlabs.online.fr/plasma/html/oa_plsm3.htm>
-   <http://van.physics.illinois.edu/qa/listing.php?id=819>
-   <http://peswiki.com/index.php/OS:Homemade_Plasma_Using_Microwave_Oven>
-   <http://www.physicsforums.com/showthread.php?t=246908>
-   <http://hackaday.com/2007/07/11/microwave-plasma/>

Microwave Reactor Design
------------------------

[//docs.google.com/document/d/1y_N8YEZ73aw19VFGPcBob5Z8TQqeujG5xQWonSaeVIA/edit Design Document: Microwave Reactor]

### Microwave Waveguides

<http://en.wikipedia.org/wiki/Horn_antenna>

Horns are necessary to smoothly impedance-match the waveguide to free space, which has a [plane wave impedance](http://en.wikipedia.org/wiki/Wave_impedance) of 377Ω.

The optimal pyramidal horn has dimensions of: \$ a_{E} = \\sqrt{2\\lambda L_{E}}, a_{H} = \\sqrt{3\\lambda L_{H}} \$

where:

\$\\lambda\$ is the wavelength

\$a_{E,H}\$ is the width of the aperature in the E-field or H-field direction

\$L_{E,H}\$ is the slant length of the side in the E-field or H-field direction

Significant microwave horn construction details are available in Chapter 18 of the ARRL Antenna Guide. From [Horn Antenna for 2.45 GHz Microwave Oven Magnetrons](http://servv89pn0aj.sn.sourcedns.com/~gbpprorg/zine2/html/55/horn.html):

    2.45 GHz Horn Dimensions
    One Wavelength at 2.45 GHz : 4.82 inches
              Target Horn Gain : 14 dB
         Gain as a Power Ratio : 25

                    "L" Length : 7.88 inches
                    "A" Length : 5.34 inches
                    "B" Length : 4.33 inches
                    "S" Length : 2.88 inches

           Waveguide's H-Plane : 3.50 inches
           Waveguide's E-Plane : 1.70 inches

### Microwave Shielding

Notes on decibel shielding: <http://www.lessemf.com/decibel.html>

EMF shielding fabrics:

-   <http://www.lessemf.com/fabric.html>
-   <http://www.westernrubber.com/products/himag-microwave-absorbers/himag-reticulated-foam-absorbers/>

Build a microwave sensor circuit:

-   <http://www.electroschematics.com/5066/giga-hertz-signal-detector/>
-   <http://www.rcgroups.com/forums/showthread.php?t=1718928>

### Modulating Microwave Output Power

Magnetron physics: <http://hyperphysics.phy-astr.gsu.edu/hbase/waves/magnetron.html>

via: <http://en.wikipedia.org/wiki/Microwave_oven>

Microwave ovens virtually always operate at 2.45GHz (wavelength = 12.2 cm)

"In most ovens, the magnetron is driven by a linear transformer which can only feasibly be switched completely on or off. As such, the choice of power level does not affect the intensity of the microwave radiation; instead, the magnetron is turned on and off in duty cycles of several seconds at a time. Newer models have inverter power supplies which use pulse width modulation to provide effectively continuous heating at reduced power so that foods are heated more evenly at a given power level and can be heated more quickly without being damaged by uneven heating."

* * * * *

via: <http://danyk.cz/magn3_en.html>

"DC powered magnetron. One MOT serves as a heating transformer, connected directly to the network. The second MOT is connected to Delon doubler, 3 + 3 capacitors and current limiter of many bulbs in series. Regulated via variac."

<http://danyk.cz/magn.html>

That's why I joined a small magnetron power only 12W. The power supply used a similar circuit as the microwave, in my case, with the motto of 700W. Power reduction is ensured by using only 16.5 nF capacitor instead of the normal capacity of about 1uF. The capacitor is constructed as MMC, composed of 20 pieces of series capacitors 330nF 275Vac. When power is 12W need MOT or cool the magnetron. Magnetron warming up takes about two seconds.

<http://danyk.cz/index_en.html>

* * * * *

via: <http://cooking.stackexchange.com/questions/7394/how-does-the-power-setting-on-a-microwave-work>

"The majority of microwaves cannot modulate their power output. The power setting in most microwaves simply turns the magnetron (microwave generator) off and in in cycles. So a power setting of .5 for 10 minutes would simply cycle the magnetron on and off every few seconds, with a total on time of 5 minutes. You can actually hear this occurring.

According to wikipedia, some newer microwaves can actually achieve a more or less constant level of reduced power using a technique called pulse-width modulation. I have never seen or used one of these though."

* * * * *

via: <http://www.vk3hz.net/amps/Microwave_Oven_Inverter_HV_Power_Supply.pdf>

"My initial reaction after measuring the voltage and current was that the output voltage from the HV PSU was extremely poorly regulated. However, when I entered the data into a spreadsheet and calculated the power, it all became clear. The power supply is delivering constant power into the load, and doing a very good job of it. (For example, at the 50% power level, with a variation of almost 50% in current drain, the power output varies by just 1 watt.) "

* * * * *

via: <http://educypedia.karadimov.info/library/Inverter.pdf>

* * * * *

via: <http://www.google.com/patents/US20040149744> "Inverter circuit of microwave oven US 20040149744 A1"

* * * * *

via: <http://www.microwaves101forum.com/showthread.php?2091-Power-adjustment-and-magnetron-longevity>

"The reason we cannot adjust the output power reliably by changing the voltage or current is that the oscillation depends critically on the trajectory of the stream of electrons leaving the heated cathode. They have to sweep around in a circle past the 6 or 8 small cavities in the block. The radius of the pitch circle of the cavity entrances is pre-determined in the manufacture, but the radius of the curved track of the electrons is determined partly by the current flow and partly by the fixed magnetic field of the permanent magnet. If the magnetic field could be adjusted as the current was reduced then the radius could be fixed to the proper design value, and the tube would oscillate but at lower power. Hence with a fixed magnetic field as on most maggies, the peak power is fixed and the only ways to vary the average output power are a) to change the on and off ratio and b) to place an attenuator between the cavity and the load or the cavity and the magnetron."

* * * * *

via: <http://www.dslreports.com/forum/r19107900-controlling-magnetron-output>

This guy wants to do EXACTLY what I want to do! He doesn't finish the project, though...

[Category: DIY](/Category:_DIY "wikilink")
