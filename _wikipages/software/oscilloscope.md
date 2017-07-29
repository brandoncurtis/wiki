---
title: Oscilloscope Interfacing
permalink: p/oscilloscope
layout: default
category: software
---

1) increase the speed of USB acquisition from the oscilloscope?

mkvirtualenv --python=$(which python3) dev3
pip install requests[security] python-usbtmc pyusb numpy matplotlib

alex.forencich
python-usbtmc 0.7
https://pypi.python.org/pypi/python-usbtmc
This Python package supports the USBTMC instrument control protocol for controlling instruments over USB.
(this is pure Python, and does not rely on the USBTMC driver)
https://github.com/python-ivi/python-usbtmc
https://github.com/alexforencich/python-usbtmc (clone of the above)
first mentioned here: https://www.raspberrypi.org/forums/viewtopic.php?f=66&t=60784&p=469648

----




http://www.righto.com/2013/07/rigol-oscilloscope-hacks-with-python.html
