---
title: MediaWiki Setup Email
permalink: /MediaWiki_Setup_Email/
---

__MATHJAX_NODOLLAR__

To allow users to confirm their registrations and reset their passwords via email, you must configure your MediaWiki (and the server it's installed on) to send emails.

Configuring Email on MediaWiki
------------------------------

First, you must install PHP mail (PEAR):

`sudo` `apt-get` `install` `php-mail`

via: [MediaWiki Manual: $wgEnableEmail](http://www.mediawiki.org/wiki/Manual:$wgEnableEmail) "MediaWiki email is almost certainly not going to work out-of-the-box on Windows servers, and it may require additional configuration on Linux servers. See Manual:$wgSMTP for information on how to configure the sending of email."

via: [MediaWiki Manual: $wgSMTP](http://www.mediawiki.org/wiki/Manual_talk:$wgSMTP#Example_using_Google_Mail)

"If this is the case, you can configure MediaWiki to use Google mail to send email from your MediaWiki site.

Set up an email account for the MediaWiki site (webmaster@mydomain.com, or info@mydomain.com), making a note of the password assigned to this account. Configure your LocalSettings.php file with the following setting, replacing "mydomain.com" with your domain name:

<code>

`    $wgSMTP = array(`
`       'host' => 'ssl://smtp.gmail.com',`
`       'IDHost' => 'mydomain.com',`
`       'port' => 465,`
`       'username' => 'webmaster@mydomain.com',`
`       'password' => 'emailpasswordforwebmaster',`
`       'auth' => true`
`    );`

</code>

You will probably also want to change these values:

`$wgEmergencyContact` `=` `"wiki@domain.org";` `$wgPasswordSender` `=` `"wiki@domain.org";`

[Category:Wiki Setup](/Category:Wiki_Setup "wikilink")
