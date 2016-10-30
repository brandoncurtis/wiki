---
template: default
title: Operational Amplifiers
permalink: p/op-amps
category: diy
---

### Current Feedback Op Amps

-   [Using current-feedback op amps for high-speed designs](http://www.embedded.com/design/other/4006793/Back-to-the-basics-Using-current-feedback-op-amps-for-high-speed-designs)
-   [The Ins and Outs of Current Feedback Amplifiers](https://www.digikey.com/Web%20Export/Supplier%20Content/Exar_1016/PDF/exar-aan-3.pdf)
-   [Voltage feedback vs. current feedback amplifiers: Advantages and limitations](https://www.ieee.li/pdf/viewgraphs/current_feedback_vs_voltage_feedback_amplifiers.pdf)
-   [What’s The Difference Between Voltage-Feedback And Current-Feedback Op Amps?](http://electronicdesign.com/analog/what-s-difference-between-voltage-feedback-and-current-feedback-op-amps)
-   [Current Feedback Amplifi er "Do’s and Dont’s"](http://cds.linear.com/docs/en/design-note/dn46fa.pdf)
-   [Wikipedia: Current-feedback operational amplifier](https://en.wikipedia.org/wiki/Current-feedback_operational_amplifier)
-   [Texas Instruments: Voltage Feedback vs. Current Feedback Op Amps](http://www.ti.com.cn/cn/lit/an/slva051/slva051.pdf)
-   [Texas Instruments: A Current Feedback Op-Amp Circuit Collection](http://www.ti.com.cn/cn/lit/an/sloa066/sloa066.pdf)

### EEVBlog Tutorials

-   [EEVblog \#727 - How To Kill An Opamp](https://www.youtube.com/watch?v=EZZcfOrcMkk)
-   [EEVblog \#490 - Peak Detector Circuit](https://www.youtube.com/watch?v=jllsqRWhjGM)
-   [EEVblog \#24 - Chopper Operational Amplifiers](https://www.youtube.com/watch?v=oibJUt6QkwI)
-   [EEVblog \#476 - Opamp Offset Voltage Measurement](https://www.youtube.com/watch?v=YeNpd-sXaHk)
-   [EEVblog \#528 - Opamp Input Noise Voltage Tutorial](https://www.youtube.com/watch?v=Y0jkPLuFdnM)
-   [EEVblog \#479 - Opamp Input Bias Current](https://www.youtube.com/watch?v=TxBJb-Z0XFI)
-   [EEVblog \#600 - OpAmps Tutorial - What is an Operational Amplifier?](https://www.youtube.com/watch?v=7FYHt5XviK)
-   [EEVblog \#572 - Cascading Opamps For Increased Bandwidth](https://www.youtube.com/watch?v=ZvT9hHG17tQ)

My Orders
---------

    instrumentation amplifier: AD8222
    precision peak detector: TS912 low bias current op amp
    chopper op amp: MAX4239

    == Instrumentation Amplifiers

    homebrew with 3x OP07D is pretty typical!

    Linear Technologies
    LT1101
    gain: fixed, 10 or 100
    single (+5V) or dual (±15V)
    LT1101AIN
    http://www.jameco.com/webapp/wcs/stores/servlet/Product_10001_10001_1729936_-1
    LT1101IN (slightly worse specs)
    http://www.jameco.com/webapp/wcs/stores/servlet/Product_10001_10001_1729979_-1
    FULLY specified for pin-strappable gains of 10x and 100x
    $19

    Analog Devices
    AD620AN
    http://www.jameco.com/webapp/wcs/stores/servlet/Product_10001_10001_115174_-1
    AD620ANZ (lead-free version of AD620AN)
    http://www.jameco.com/webapp/wcs/stores/servlet/Product_10001_10001_1780862_-1
    AD620B (less gain error and less voltage offset than AD620A)
    op amps: 1
    gain:   1       (1000 kHz)
            10      (800 kHz)
            100     (120 kHz)
            1000    (12 kHz)
    input bias current: 2 nA max
    supply: dual (±2.3V to ±18V)
    http://www.jameco.com/Jameco/Products/ProdDS/115174.pdf
    higher CMR and lower input bias current than AD623
    $7

    Analog Devices
    AD621ANZ (lead-free)
    gain: fixed, 10 or 100
    bandwidth: 800kHz (G=10) or 200kHz (G=100)
    supply: dual (±2.3V to ±18V)
    op amps: 1
    http://www.jameco.com/webapp/wcs/stores/servlet/Product_10001_10001_1780918_-1
    http://www.jameco.com/Jameco/Products/ProdDS/1780918.pdf
    FULLY specified for pin-strappable gains of 10x and 100x
    $12

    Analog Devices
    AD623
    gain: 1 fixed to 1,000
    bandwidth: 800kHz @ G=1
    input bias current: 25 nA max
    single (+3 to +12V) or dual (±2.5V to ±6.0V)
    AD623ANZ (lead-free
    http://www.jameco.com/webapp/wcs/stores/servlet/Product_10001_10001_1780985_-1
    http://www.jameco.com/Jameco/Products/ProdDS/1780985.pdf
    specifically listed for industrial process control and transducer/thermocouple/acquisition/difference amplifiers
    optimized for single-supply use; gain set with a single resistor
    $5

    Texas Instruments
    INA126
    http://www.jameco.com/webapp/wcs/stores/servlet/Product_10001_10001_825934_-1
    http://www.jameco.com/Jameco/Products/ProdDS/825934.pdf
    supply: dual (±1.35V to ±18V)
    op amps: 1
    gain:   5       (200 kHz)
            10      (9 kHz)
            500     (1.8 kHz)
    input bias current: 10nA
    $3

    Analog Devices
    AD823
    supply: single (3V to 36V) or dual (±1.5V to ±18V)
    input bias current: <25 pA
    devices per package: 2x
    single- or dual-supply JFET input rail-to-rail high-speed general-purpose
    http://www.jameco.com/webapp/wcs/stores/servlet/Product_10001_10001_1791668_-1
    http://www.jameco.com/Jameco/Products/ProdDS/1791668.pdf
    $7.15

    let's buy 2x AD623 (single-supply), 2x AD620 (dual-supply), 4x INA126  (cheapo low-bandwidth dual supply), 2x AD823 (dual-supply JFET input rail-to-rail high-speed)
    ----
    TEXAS INSTRUMENTS
    TLE2142
    gain-bandwidth product: 5.9MHz
    single (+4 to +44V) or split
    http://www.jameco.com/webapp/wcs/stores/servlet/Product_10001_10001_2002771_-1
    $3.09
