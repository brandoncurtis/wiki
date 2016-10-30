---
title: Non-Contact Temperature Measurement
permalink: /Non-Contact_Temperature_Measurement/
---

Technical Challenges
--------------------

[Leslie's cube](https://en.wikipedia.org/wiki/Leslie_cube) and the importance of [surface emissivity](https://en.wikipedia.org/wiki/Emissivity#Emissivities_of_common_surfaces)

Measurement Hardware
--------------------

### Melexis Thermopile

BC DOCUMENTS (access may be restricted):

-   [Melexis MLX90614 Thermopile](https://docs.google.com/document/d/1q1zOrZD-xRPg58K0y3EioUk-HojLw50pNjn3hNCJPwU/edit#heading=h.ann1qekudz7t)

#### Description

-   Melexis MLX digital thermopile purchased from Digikey (~$20)
-   0.5°C accuracy, 0.02°C resolution, 10° FOV
-   SMBus digital output; PWM output for continuous reading
-   <http://www.digikey.com/product-detail/en/MLX90621ESF-BAB-000-TU/MLX90621ESF-BAB-000-TU-ND/4968086>
-   <https://groups.google.com/forum/#!topic/flir-lepton/Kpq1HZYGZ2U>

#### MLX90614 on the Raspberry Pi

### Thermopile IR Cameras

    < to research! >

### FLIR Lepton Long-Wave IR Camera

#### Example Code

<https://bitbucket.org/brandoncurtis/lepton-camera> <https://github.com/brandoncurtis/DIY-Thermocam> <https://github.com/brandoncurtis/go-lepton>

#### Description

-   <https://www.sparkfun.com/products/13233>
-   <https://learn.sparkfun.com/tutorials/flir-lepton-hookup-guide>
-   <https://github.com/groupgets/LeptonModule>
-   <https://groups.google.com/forum/#!searchin/flir-lepton/radiometry$20%7Csort:relevance/flir-lepton/uw9XKkOllis/iAsFgb_jRhUJ>
-   <http://www.theresistornetwork.com/2014/11/flir-lepton-thermal-imaging-sensor.html>

#### Outstanding Questions

-   Can you change the optic to convert between 51° and 25° FOV?
-   Can you install a shutter on a non-shuttered Lepton?
-   Open alternatives to the Lepton?
-   What does Flat Field Correction actually do?

<!-- -->

    EXAMPLES
    http://hackaday.com/2015/12/25/build-your-own-thermal-camera/
    http://www.diy-thermocam.net/
    https://groups.google.com/forum/#!msg/flir-lepton/zZoSEaE-mWA/F7H5ZI-hEwAJ
    https://groups.google.com/forum/#!topic/flir-lepton/qzetjSykLpQ

    DESCRIPTIONS OF TEMPERATURE CALCULATIONS
    https://groups.google.com/forum/#!topic/flir-lepton/ZhXGJvLWSiI
    "I am doing this and it works quite good, but you need to use a separate single-point IR sensor to do the correlation.
    For my application, I use a MLX90614 with 5° FOV (BCI or DCI).
    To get ambient temperature independant raw values from the Lepton, you need to activate Radiometry mode over I2C. Otherwise, you need to redo the calibration if the ambient temperature changes too much.
    For the calibration proccess, I point the IR sensor to the middle of the FOV of the Lepton and then take 100 different samples. That takes about 10 seconds. Afterwards, I use a methamtical method called "Least square fit" to get the first grade calibration formula (y = ax + b)
    There are implementations of this method for any programming languages on the web, just google it. As soon as you have the calibration formula, you can then go ahead and calculate the absolute temperature for every pixel on the Lepton ! Of course the accuracy depends on the objects used in the calibration procces, so if you use different hot and cold objects, it should be quite good.
    I hope that was helpful"

    Well, all of FLIR's other cameras use 'RBFO' values in order to convert raw signal values into meaningful temperature readings.  The relationship is non-linear (hence a line of best fit will only work over a small range of temperatures).
    So Temperature in Kelvin is equal to:
    T = B / Ln ( R / (RawVal - O) + F)
    Look at FLIR's Gev Demo source code for hints http://80.77.70.144/SwDownload/Assets/ThermoVision/PvSample.zip

    Alex is right, that proccess also applies to the FLIR Lepton. There is a document under NDA called "FLIR Lepton Radiometry Application Note" that describes it.
    What I also do is leave B and F at its default values and do a least square fit for R and O. I use 100 calibration samples between several lepton pixels multiplied by a weight matrix to build an average raw value and real temperatures from a MLX90614 ir sensor pointing to that average value as inputs.
    ----
    UCSB

    "smartvision"
    Jacob Anderson, William Chen,
    Christopher Kim, Jonathan Simozar,
    Brian Wan
    https://capstone.cs.ucsb.edu/
    NovaToast SmartVision

    https://capstone.cs.ucsb.edu/team_docs_15/prd2/NovaToast_PRD2.pdf
    "The data from the Lepton is read in as a stream of 4,800 14­bit values, making an 80x60
    image. Each value represents a 12­bit color with a 2­bit pad."

    "The Lepton is a longwave infrared imaging sensor. The particular model used has no shutter,
    so it works from calibration, meaning, once calibrated, it will be able to detect temperatures
    colder or hotter than the object which it was calibrated to. With the potential addition of a
    shutter, it will be able to be accurately calibrated every time. RBFO calibration values will be
    read from the Lepton and used in various radiometry algorithms to obtain an absolute
    temperature value. The Lepton sends the image as a stream of bits over a serial connection
    which is then pieced together in the Pi."

    https://angel.co/projects/138302-smartvision
    https://capstone.cs.ucsb.edu/past15ws.html#team2
    https://vimeo.com/121842781

    William Chen
    UNIVERSITY OF CALIFORNIA, SANTA BARBARA · 2015
    Bachelor of Science, Computer Engineering
    https://angel.co/william-chen-3
    https://www.linkedin.com/in/hellowilliamchen
    https://www.facebook.com/william.chen.3597
    https://github.com/Chilliam

    Brian Wan
    https://angel.co/brian-wan
    https://www.linkedin.com/in/bmwan
    ----
    FLIR RBFO

    "Advanced Radiometry" application note on another FLIR camera
    http://www.teax-tec.de/thermalcapture-web/wp-content/uploads/2015/02/FLIR_Advanced_Radiometry_Note.pdf
    ----
    What is Frame Telemetry?
    https://en.wikipedia.org/wiki/Frame_synchronization
    "In telecommunication, frame synchronization or framing is the process by which, while receiving a stream of framed data, incoming frame alignment signals (i.e., a distinctive bit sequences or syncwords) are identified (that is, distinguished from data bits), permitting the data bits within the frame to be extracted for decoding or retransmission."

    http://www.storm.com/telemetry_tutorial/r_frame_synchronization.html
    ----
    https://groups.google.com/forum/#!topic/flir-lepton/ZhXGJvLWSiI

    "I am doing this and it works quite good, but you need to use a separate single-point IR sensor to do the correlation.
    For my application, I use a MLX90614 with 5° FOV (BCI or DCI).
    To get ambient temperature independant raw values from the Lepton, you need to activate Radiometry mode over I2C. Otherwise, you need to redo the calibration if the ambient temperature changes too much."
    ----
    FLIR Lepton Knowledge Base
    http://www.flir.com/cvs/cores/knowledgebase/index.cfm?level=2&CFTREEITEMKEY=914

    "The digital output of Lepton is 14-bit raw data, only."
    "Information about Lepton that FLIR puts in the public domain can be found at www.flir.com/cvs/cores/view/?id=62648 and at the FAQ or Knowledge Base."
    "Yes, Lepton utilizes FLIR's proprietary scene-based non-uniformity compensation (NUC)."
    "Yes, scene-based non-uniformity compensation (SBNUC) is enabled in Lepton."
    "The Set RAD RBFO External Parameters command is not currently used, and should not be sent by the user. This command is reserved for future Lepton use."

    Can Lepton's automatic flat-field correction (FFC) be disabled?
    "Yes, there are three flat-field correction modes for Lepton. For cameras with a shutter, FLIR sets the default at the factory to FFC, but it is possible to change the mode to manual FFC. (The third mode is for commanding FFC without using the integral shutter.) The mode is selected using the SYS FFC Mode Control Command, described in Section 4.5.15 of the software IDD. In manual mode, the camera will not perform FFC until commanded."
    "The default value of Lepton's flat-field correction (FFC) time trigger is 300 seconds (5 minutes)."
    "Note that Lepton only has a single NUC table, so automatic table changing is not applicable."

    "You should wait at least 700 milliseconds from releasing reset at power-up before sending I2C commands to the Lepton module."

    "Some settings, including AGC and telemetry state, are accessible to and may be changed by the user. The frame rate, exposure, gain, and noise settings cannot be changed for Lepton — these are factory-set, fundamental camera operating characteristics that define Lepton operation."

    "Availability of Radiometry commands is restricted to Original Equipment Manufacturer (OEM) customers for Lepton, and requires that an active non-disclosure agreement (NDA) be in place with FLIR."

    "The Software IDD for each Lepton version defines its features and describes how to use them. The Lepton 3.5 release slated for production in the fall of 2015 will offer full radiometry. The Lepton 3 vs. Lepton 2 Application Note describes the general differences and feature sets for each Lepton release. To use radiometry, the recommended procedure is to use a shutter or uniform temperature source in front of the Lepton to calibrate the camera."

    "FLIR plans to introduce a full radiometric Lepton solution in late 2015. The Software IDD for each Lepton version defines its features. If temperature measurement or another radiometric feature is not described in the IDD provided for a given version, then that version does not have that feature."

    "The depth of field is 10 cm to infinity for the standard 51-degree 80x60 Lepton."

    "Lepton radiometric calibration tables are burned into one time programmable (OTP) memory for each individual camera. There are currently no Lepton cameras which have radiometric calibration other than the limited function mentioned in the datasheet. This stabilizes the camera output over changes in camera temperature, but does not provide temperature conversion."

    "How linear is Lepton's temperature range between 20-40 degrees using the radiometric mode?
    The data is approximately linear with the power received, not with scene temperature. There are no specifications on the linearity of Lepton's data output."

    "Periodic flat-field corrections or FFCs should be done at power up and as Lepton's temperature changes. Some Lepton configurations are available with an integrated shutter that performs the FFC automatically. Calibration beyond FFCs would be specific to an application."

    "Periodic flat-field corrections or FFCs should be done at power up and as Lepton's temperature changes. Some Lepton configurations are available with an integrated shutter that performs the FFC automatically. Calibration beyond FFCs would be specific to an application."

    "There are three field of view (FoV) models planned for the Lepton 160x120, listed in order of pending availability: a 56 degree; a 95 degree; and a 25 degree."

    "For applications that require imaging scene temperature ranges higher than 550 C, it is necessary to reduce the signal coming into the camera sensor in order to avoid image saturation. This is typically done by using an external filter to attenuate the signal and put it in a range that the camera can handle. Neutral density (ND) filters work well for this purpose. For example, an ND 1.0 filter has a transmittance of 10%, which it accomplishes using a combination of absorption and reflection.

    Using an ND 1.0 filter, it should be possible to image scene temperature ranges up to ~2,800C, since the 10% transmittance would attenuate the radiance signal within the Low Gain limit of 550 C.

    A filter holder has been designed that screws onto the front of the lenses for Tau lenses that are threaded. It holds 1 inch diameter filters. Spectrogon is one source of LWIR ND filters.

    Note that some FLIR cameras are specially calibrated to provide radiometric (temperature) data on a per-pixel basis, and use of external optics such as filters will invalidate the temperature results. A separate radiometric calibration would be required with a filter in place for better accuracy."
    ----
    https://bitbucket.org/brandoncurtis/lepton-camera
    ----
    ADDITIONAL FLIR LEPTON RESOURCES

    FLIR thermal camera with Propeller? It works!
    http://forums.parallax.com/discussion/162400/flir-thermal-camera-with-propeller-it-works

    IRLYNX Shutterless radiometric kit with FLIR LEPTON - Focus on Stability during 10mn
    https://www.youtube.com/watch?v=2Fbbsiqith4

    Yet another cheap thermal imager incoming.. Seek Thermal
    http://www.eevblog.com/forum/thermal-imaging/yet-another-cheap-thermal-imager-incoming/2210/?wap2

    Flir One Thermal imaging camera teardown and hacks
    http://www.eevblog.com/forum/thermal-imaging/flir-one-thermal-imaging-camera-teardown-and-hacks/

    https://www.reddit.com/r/AskEngineers/comments/3djo0d/in_general_do_thermal_cameras_like_the_flir/
    In general, do thermal cameras like the Flir Lepton have better thermal sensitivity when the camera itself is at a colder temperature? Basically, wondering how to get as much sensitivity out of my Lepton as possible.

    DroneThermal Analog MAV Cameras, Almost Ready
    http://diydrones.com/profiles/blogs/dronethermal-mav-cameras-almost-ready
    "We signed the agreements with FLIR for Lepton thermal camera cores as well. "

    LeptonDemo
    http://www.pureengineering.com/projects/leptondemo

    Pure Engineering: Lepton
    http://www.pureengineering.com/projects/lepton

    How to enable the radiometry mode?
    https://groups.google.com/forum/#!topic/flir-lepton/-1YYPLr6TrQ
    (includes comments by irlynx and DIY-Thermocam)