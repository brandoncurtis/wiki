---
template: default
title: Power Supplies
permalink: p/power-supplies
category: diy
---

Voltage Converter ICs
---------------------

    LTC1046 - inductorless 5V to -5V convertoer (Jameco $6.75)
    MAX1044 - switched-capacitor voltage converters (pin-compatible with ICL7660, LT1044) (Digikey $3)
    MAX660 - similar to MAX1044, but supports more current (100mA vs 10mA) (Digikey, $1.50)
    LTC7149 - Vin 3.4 to 60V;
    LTC3649 - Vin 3.1 to 60V; Vout 0 to Vin-0.5V; Digikey $12
    LTC3896 - Vin 36 to 72V; Vout 0 to -48V; Digikey $10

    MAX660 can be cascaded! 2x → 11.0Vout
    from MAX1044 datasheet: "Three or more devices can be cascaded in this way, but output impedance rises dramatically... a better solution may be an inductive switching regulator, such as MAX755, MAX759, MAX764, MAX774."

Split-Rail Power Supply
-----------------------

<http://forum.allaboutcircuits.com/threads/split-rail-power.69073/>

<http://forum.allaboutcircuits.com/threads/creating-a-virtual-power-supply-article.13678/#post-84026>

<http://electronics.stackexchange.com/questions/79307/what-are-the-ways-to-make-a-dual-power-supply-from-a-single-voltage-source>
