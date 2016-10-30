---
layout: default
title: Sage Math
permalink: p/sage-math
category: software
---

Sage Math is a free, open-source computer algebra system. You can install it on any device and do any kind of math at no cost!

SageMathCloud
-------------

<http://aperiodical.com/2013/09/computational-mathematics-in-the-cloud-with-sagemath/>

<https://troymcnotebook.wordpress.com/edit-and-render-latex-documents-online/>

<http://sagemath.blogspot.com/2013/08/latex-in-cloud.html>

Installing Sage
---------------

\[ Brandon's Sage Math installation guide\]

### ffmpeg replacement

ffmpeg no longer has an installation candidate in the Ubuntu 14.04 repositories:

<http://askubuntu.com/questions/432542/is-ffmpeg-missing-from-the-official-repositories-in-14-04>

<http://ubuntuhandbook.org/index.php/2014/01/install-latest-ffmpeg-2-1-2-ubuntu-ppa/>

Your options:

    NOTE: will not work if you reference ffmpeg in your code!

    sudo apt-get install libav-tools

    sudo add-apt-repository ppa:mc3man/trusty-media
    sudo apt-get update
    sudo apt-get install ffmpeg gstreamer0.10-ffmpeg

    NOTE: doesn't provide GStreamer-ffmpeg integration!

    sudo apt-add-repository ppa:jon-severinsson/ffmpeg
    sudo apt-get update
    sudo apt-get install ffmpeg

Using Sage
----------

Please see my [Sage Math tutorials](http://sage.brandoncurtis.com) for an introduction to what Sage can do.

Publishing from Sage
--------------------

Question:

    Is there an easy way to publish Sage documents and their output to PDFs/LibreOffice documents so that I can edit and comment on them to turn in as homework?

Answer:

    SageMathCloud notebook:
    You can use markdown (https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) or html right inside a notebook cell by typing %md or %html at the beginning of the cell; when evaluated, it'll hide the markup and display the results.  You can use this to comment up your work.  SageMathCloud has a Print button too, just to the left of 'History' and 'Save' (see attachment).  Worksheets can also be published publicly and viewed by anyone: http://goo.gl/m6gl1N

    Local Install notebook:
    %md hasn't been added to the latest release, but %html has; you can also insert richtext cells.  The 'Print' button is the leftmost in the view selection ribbon.

    Terminal Mode (local or cloud):
    A final option is to do everything in text in the terminal and output any graphics with .save('filename').  The text can then be copied-and-pasted and the images inserted into your word processor of choice.

    SageMathCloud also has a fully-functional LaTeX editor built in.  SageTex brings it all together: http://www.sagemath.org/doc/tutorial/sagetex.html
