---
title: MediaWiki Setup Preventing Vandalism
permalink: "/MediaWiki_Setup_Preventing_Vandalism/"
---

To cut down on spam and vandalism, this site uses a number of suggestions from [Cookipedia - How to stop Spam on a MediaWiki](http://www.cookipedia.co.uk/recipes_wiki/How_to_stop_Spam_on_a_MediaWiki). See also the [Mediawiki:Combating Spam](http://www.mediawiki.org/wiki/Manual:Combating_spam) and [MediaWiki:Combating Vandalism](http://www.mediawiki.org/wiki/Manual:Combating_vandalism).

Antispam Additions to LocalSettings.php
---------------------------------------

    #######################
    ### ANTISPAM TWEAKS ###
    #######################

    ### The Nuclear Options ###
    # These options make the site much less wiki-like
    # They are not recommended!

    # Anonymous users cannot edit
    #$wgGroupPermissions['*']['edit'] = false;

    # Anonymous users cannot create new pages
    #$wgGroupPermissions['*']['createpage'] = false;

    # Users must email-confirm before editing
    #$wgEmailConfirmToEdit = true;

    ### More Reasonable Restrictions ###

    # Limit the number of accounts that can be created from a single IP address in a 24-hour period
    # this can help stem the tide in the event of a mass spam attack
    # requires memcached!
    $wgAccountCreationThrottle = 2;

    # enable CheckUsers (link usernames to IP addresses)
    require_once "$IP/extensions/CheckUser/CheckUser.php";

    # enable UserMerge (merge junk accounts for deletion)
    require_once "$IP/extensions/UserMerge/UserMerge.php";
    $wgGroupPermissions['bureaucrat']['usermerge'] = true;

    # enable and configure ConfirmEdit (captchas); bundled with MediaWiki
    # use QuestyCaptcha—requires users to answer admin-defined questions
    require_once "$IP/extensions/ConfirmEdit/ConfirmEdit.php";
    require_once "$IP/extensions/ConfirmEdit/QuestyCaptcha.php";
    $wgCaptchaClass = 'QuestyCaptcha';

    # define the QuestyCaptcha questions and answers
    $arr = array (
            'In English, what animal is this? <img src="http://upload.wikimedia.org/wikipedia/commons/thumb/5/57/7weeks_old.JPG/320px-7weeks_old.JPG">' => 'dog',
        'In English, what animal is this? <img src="http://upload.wikimedia.org/wikipedia/commons/thumb/d/d4/Rotze_Bert.jpg/320px-Rotze_Bert.jpg">' => 'cat',
        'In English, what animal is this? <img src="http://upload.wikimedia.org/wikipedia/commons/thumb/f/f1/Hen_0001.jpg/320px-Hen_0001.jpg">' => 'chicken',
        'In English, what animal is this? <img src="http://upload.wikimedia.org/wikipedia/commons/thumb/9/90/Vache_Aubrac.jpg/320px-Vache_Aubrac.jpg">' => 'cow'
    );

    foreach ( $arr as $key => $value ) {
            $wgCaptchaQuestions[] = array( 'question' => $key, 'answer' => $value );
    }
    $wgCaptchaTriggers['edit']          = true; # captcha required when editing pages
    $wgCaptchaTriggers['create']        = true; # captcha required when creating pages
    $wgCaptchaTriggers['addurl']        = true; # captcha required when adding URLS to a page
    $wgCaptchaTriggers['createaccount'] = true; # captcha required when creating an account
    $wgCaptchaTriggers['badlogin']      = true; # captcha required after multiple failed login attempts

    # if a user has confirmed their account via email, allow them to skip the captchas
    $wgGroupPermissions['emailconfirmed']['skipcaptcha'] = true;
    $ceAllowConfirmedEmail = true;

Need to install Memcached? Check out [Installing Memcached for MediaWiki](/Installing_Memcached_for_MediaWiki "wikilink").

Deleting Spam Pages
-------------------

When spam DOES get through, [the Nuke MediaWiki extension](https://www.mediawiki.org/wiki/Extension:Nuke) is your best friend!

Install it and use it to mass-delete spam pages with a simple interface.

Deleting Spam Users
-------------------

The standard advice is to use PHP requests to edit the database, but your site is hosed if you screw this up.

A safer option: the [User Merge & Delete extension](http://www.mediawiki.org/wiki/Extension:User_Merge_and_Delete) or the [Remove Unused Accounts](http://www.mediawiki.org/wiki/Manual:RemoveUnusedAccounts.php) maintenance script. Maintenance scripts come with MediaWiki by default; run this one with:

`sudo` `php` `maintenance/removeUnusedAccounts.php` `--conf` `LocalSettings.php`

For use instructions, see [TrailWiki Delete Spam Users.](http://www.trailwiki.org/wiki/Help:Delete_Spam_Users)

If you're cleaning up after a major spam attack, it may help to run the Delete Archived Revisions maintenance script first:

`sudo` `php` `maintenance/deleteArchivedRevisions.php` `--conf` `LocalSettings.php` `--delete`

Further Foiling Spammers
------------------------

Use the [ConfirmEdit extension](http://www.mediawiki.org/wiki/Extension:ConfirmEdit) to require users to solve a math problem, fill out a CAPTCHA, or the like before they may edit a page. This extension is included by default in modern MediaWiki setups, so all you have to do is enable and configure it. This extension can also be used to require successful completion of a CAPTCHA to register a user account.

Use the [CheckUser extension](http://www.mediawiki.org/wiki/Extension:CheckUser) to collect spammer IP addresses to block.

Use the [SpamBlacklist extension](http://www.mediawiki.org/wiki/Extension:SpamBlacklist) to prevent users from linking to known spam sites.

[Category:Wiki Setup](/Category:Wiki_Setup "wikilink")
