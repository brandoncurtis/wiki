---
title: MediaWiki Setup: Images
permalink: /MediaWiki_Setup:_Images/
---

Standard Setup
--------------

    ## To enable image uploads, make sure the 'images' directory
    ## is writable, then set this to true:
    $wgEnableUploads  = true;
    $wgUseImageMagick = true;
    $wgImageMagickConvertCommand = "/usr/bin/convert";
    $wgFileExtensions = array( 'png', 'gif', 'jpg', 'jpeg', 'doc',
        'xls', 'mpp', 'pdf', 'ppt', 'tiff', 'bmp', 'docx', 'xlsx',
        'pptx', 'ps', 'odt', 'ods', 'odp', 'odg'
    );

Details
-------

-   <http://www.mediawiki.org/wiki/Manual:$wgMaxUploadSize>
-   <http://www.mediawiki.org/wiki/Manual:Configuring_file_uploads#Set_maximum_size_for_file_uploads>

To allow uploading of larger files, edit these parameters in php.ini:

post_max_size,\[1\] 8 megabytes large by default upload_max_filesize,\[2\] 2 megabytes large by default

sudo nano /etc/php5/apache2/php.ini

sudo nano /etc/mediawiki/wiki-ahs/LocalSettings.php

add this:

$wgMaxUploadSize = 1024\*1024\*10;

<http://www.mediawiki.org/wiki/Help:Images>

to change the size of an embedded image:

    [[/file:blahblah.jpg|800px]]

[Category:Wiki Setup](/Category:Wiki_Setup "wikilink")

__MATHJAX_NODOLLAR__