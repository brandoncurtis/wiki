---
title: MediaWiki Setup Google Analytics
permalink: "/MediaWiki_Setup_Google_Analytics/"
---

Google Analytics Integration
----------------------------

You'll need to install the [Google Analytics Integration extension](https://www.mediawiki.org/wiki/Extension:Google_Analytics_Integration).

You'll also need to add something like this to your Local_Settings.php:

    ##############################
    ### Google Analytics Setup ###
    ##############################

    require_once "$IP/extensions/googleAnalytics/googleAnalytics.php";
    // Replace xxxxxxx-x with YOUR GoogleAnalytics UA number
    $wgGoogleAnalyticsAccount = "UA-xxxxxxx-x";
    // Optional Variables (both default to true)
    #$wgGoogleAnalyticsIgnoreSysops = false;
    #$wgGoogleAnalyticsIgnoreBots = false;
    // If you use AdSense as well and have linked your accounts, set this to true
    $wgGoogleAnalyticsAddASAC = false;

[Category:Wiki Setup](/Category:Wiki_Setup "wikilink")
