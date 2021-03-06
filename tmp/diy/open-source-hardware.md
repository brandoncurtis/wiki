---
title: Open Source Hardware
permalink: p/open-source-hardware
layout: default
category: diy
---

Arduino
-------

[The Making of Arduino](http://spectrum.ieee.org/geek-life/hands-on/the-making-of-arduino/0)

-   Adafruit - Learn Arduino <https://learn.adafruit.com/category/learn-arduino>
-   Sparkfun - Learn <https://learn.sparkfun.com/>
-   Arduino Tutorials <http://arduino.cc/en/Tutorial/HomePage>
-   Instructables - Arduino <http://www.instructables.com/id/Arduino-Projects/>
-   Makezine - Arduino <http://makezine.com/category/electronics/arduino/?post_type=projects>

I highly recommend introducing sensors as early as possible: [<http://www.jameco.com/webapp/wcs/stores/servlet/StoreCatalogDrillDownView?langId>=-1&storeId=10001&catalogId=10001&categoryName=cat_1510&subCategoryName=Opto%20%26%20Illumination%20%2F%20Opto%20Components%20%2F%20Photocells%2C%20CDS&category=151080&refine=1&position=1&history=xz4vdsve%7Ccategory\~15%5EcategoryName\~category_root%5EsubCategoryName\~Opto%2B%2526%2BIllumination%409xn7fr68%7Ccategory\~1510%5EcategoryName\~cat_15%5Eposition\~1%5Erefine\~1%5EsubCategoryName\~Opto%2B%2526%2BIllumination%2B%252F%2BOpto%2BComponents%5EprodPage\~15%5Epage\~SEARCH%252BNAV CdS photocells] and [<http://www.jameco.com/webapp/wcs/stores/servlet/StoreCatalogDrillDownView?langId>=-1&storeId=10001&catalogId=10001&categoryName=cat_1070&subCategoryName=ICs%20%26%20Semiconductors%20%2F%20Transistors%20%2F%20Thermistors&category=107039 NTC thermistors] are cheap and durable and provide instant access to light and temperature.

Don't forget LEDs and breadboards :D

Everywhere also has their own version of an [Arduino Starter Kit](http://www.jameco.com/webapp/wcs/stores/servlet/Product_10001_10001_2171188_-1).

### Useful Shields

Arduino Motor Shield v2

-   <https://learn.adafruit.com/adafruit-motor-shield-v2-for-arduino/install-headers>

Arduino Stacking Headers

-   <https://www.jameco.com/webapp/wcs/stores/servlet/Product_10001_10001_2137756_-1>
-   <http://www.jameco.com/webapp/wcs/stores/servlet/Product_10001_10001_2144614_-1>
-   <http://www.jameco.com/webapp/wcs/stores/servlet/Product_10001_10001_2144631_-1>

Arduino-Compatible Headers, non-stacking

### Light Sensing and Simple Control

This sketch uses a photodiode and a resistor to measure ambient light intensity. The intensity is recorded onto an SD card using an Ethernet Shield. The LED on Arduino also blinks at a rate proportional to the light intensity.

    #include <SD.h>

    /*
      Analog Input
     Demonstrates analog input by reading an analog sensor on analog pin 0 and
     turning on and off a light emitting diode(LED)  connected to digital pin 13.
     The amount of time the LED will be on and off depends on
     the value obtained by analogRead().

     The circuit:
     * Ethernet Shield with SD card
     * Potentiometer attached to analog input 0
     * center pin of the potentiometer to the analog pin
     * one side pin (either one) to ground
     * the other side pin to +5V
     * LED anode (long leg) attached to digital output 13
     * LED cathode (short leg) attached to ground

     * Note: because most Arduinos have a built-in LED attached
     to pin 13 on the board, the LED is optional.


     Created by David Cuartielles
     modified 30 Aug 2011
     By Tom Igoe

     This example code is in the public domain.
     http://arduino.cc/en/Tutorial/AnalogInput
     */

    int sensorPin = A0;    // select the input pin for the potentiometer
    int ledPin = 13;      // select the pin for the LED
    int sensorValue = 0;  // variable to store the value coming from the sensor
    File myFile;

    void setup() {
      // declare the ledPin as an OUTPUT:
      pinMode(ledPin, OUTPUT);
      SD.begin(4);
      pinMode(10,OUTPUT);
    }

    void loop() {
      // read the value from the sensor:
      sensorValue = analogRead(sensorPin);
      // turn the ledPin on
      digitalWrite(ledPin, HIGH);
      // stop the program for <sensorValue> milliseconds:
      delay(sensorValue);
      // turn the ledPin off:
      digitalWrite(ledPin, LOW);
      // stop the program for for <sensorValue> milliseconds:
      delay(sensorValue);
      myFile=SD.open("test.txt",FILE_WRITE);
      myFile.println(sensorValue,DEC);
      myFile.close();
    }

### Arduino-Based Oscilloscope

From [//docs.google.com/document/d/18SpGbboyXHWd04xeR2Na5LScBEVtYuW1DqWI6rWWIJ0/edit\# Google Docs]:

Use the ‘AnalogReadSerial’ Arduino example sketch to send an analog voltage reading to the computer:

    /*
      AnalogReadSerial
     Reads an analog input on pin 0, prints the result to the serial monitor

     This example code is in the public domain.
     */

    void setup() {
      Serial.begin(9600);
    }

    void loop() {
      Serial.println(analogRead(A0));
    }

Use this python program to receive the data on the computer and graph it: (note this requires the ‘matplotlib’ module — apt-get install python-matplotlib)

    import serial, numpy, matplotlib
    from time import sleep
    port = '/dev/ttyACM0'
    ser = serial.Serial(port,9600,timeout=0)
    f = open('/tmp/workfile', 'w')
    i = 0
    while i<500:
        data = ser.read(9999)
        if len(data) > 0:
                f.write(data)
        i = i+1

    data = numpy.genfromtxt('/tmp/workfile')
    import matplotlib.pyplot as plt
    z = plt.plot([])
    z += plt.plot(data)
    plt.show()

With a wire across the 555 terminal in place of a resistor, the LED is clearly blinking violently. The graph:

((insert graph here!))

Can I increase the baud rate above 9600 on the Arduino? <http://arduino.cc/en/Serial/Begin>

I currently use:

Serial.begin(9600);

As it turns out, all I have to do is use:

Serial.begin(115200);

possible baud rates: 300, 600, 1200, 2400, 4800, 9600, 14400, 19200, 28800, 38400, 57600, or 115200

After making the same adjustment in the Python script:

((insert second graph!))

According to this: <https://sites.google.com/site/measuringstuff/the-arduino#TOC-Sample-Rates> with this setup, I’m sampling around 500 times per second. I can add timestamps by printing ‘micros()’. As the site mentions, you can use Arduino memory magic to get up to 56k samples per second! But you’re still limited to only 100 samples by the onboard memory... must get an Arduino with a memory card!

### Arduino References

Information on the pySerial module:

-   <http://pyserial.sourceforge.net/pyserial_api.html>

High-speed sampling with the Arduino:

-   <https://sites.google.com/site/measuringstuff/the-arduino#TOC-Sample-Rates>
-   <http://www.geocomputing.co.uk/getpage.php?type=page&page=megaspeedtest>
-   <http://forum.arduino.cc/index.php/topic,6549.0.html>

Python i/o tutorial:

-   <http://www.tutorialspoint.com/python/python_files_io.htm>

Python pyserial module:

-   <http://pyserial.sourceforge.net/pyserial_api.html>

Arduino serial information:

-   <http://arduino.cc/en/Serial/Begin>

Sensing and Control
-------------------

### Electrical Conductivity

-   [//www.sparkyswidgets.com/portfolio-item/miniec-i2c-ec-interface/ MiniEC]
-   [//www.sparkyswidgets.com/portfolio-item/isolated-ec-interface/ IsoEC]

### pH

-   [//www.sparkyswidgets.com/portfolio-item/miniph-i2c-ph-interface/ MinipH]

### Ion-Selective Electrodes

-   [//www.sparkyswidgets.com/portfolio-item/ion-selective-electrode-interface/ isoIon]

### Sensor Resources

-   [//www.openreefs.com/ OpenReefs]
-   [//www.atlas-scientific.com/ Atlas Scientific]
-   [//www.sparkfun.com/products/11194 DO, Atlas Scientific]
-   [//www.instructables.com/id/Arduino-Aquaponics-EnvDAQ-Upgrade-with-pH-and-Diss/ Arduino Aquaponics: EnvDAQ Upgrade with pH and Dissolved Oxygen]
-   [//www.iowa-aquaponics.com/arduino/\#GoogleAppEngine Iowa Aquaponics]
-   <http://www.synbio.org.uk/hardware.html>
-   <http://www.openlabtools.org/>
-   <http://makespace.org/>
-   <http://www.raspberrypi.org/>

Facebook's Open-Source Networking
---------------------------------

<https://code.facebook.com/posts/717010588413497/introducing-6-pack-the-first-open-hardware-modular-switch/>

[Category: DIY](/Category:_DIY "wikilink")

__MATHJAX_NODOLLAR__
