---
title: Inserting Special Characters with Unicode
permalink: /Inserting_Special_Characters_with_Unicode/
---

It is VERY slow going to type something up that contains large numbers of nonstandard symbols if you rely on the 'insert special characters' menus in Microsoft Word or Google Docs. Fortunately, there is a better way.

Windows
-------

### ALT codes

Windows supports typing of Unicode characters by holding the 'alt' key and typing a character code on the numeric pad. If you type the character code alone, for instance 'alt 169', the symbol from the so-called 'Code Page 437' (original IBM) will be inserted: ⌐

<http://en.wikipedia.org/wiki/Code_page_437>

If you type the character code preceded by a zero, for instance 'alt 0169', the symbol from the so-called 'Windows-1252' (Latin code page) will be inserted: ©

<http://en.wikipedia.org/wiki/Windows-1252>

If you type a number higher than 0255, it wraps back around to the beginning (for instance, alt 0304 yields '0'; 304 - 256 = 48, the Windows-1252 code for zero).

As you can probably see, the contents of these two codepages is fairly limited. If you want to insert a 'delta' or another greek character, for instance, you're out of luck with this method. There is, however, another way!

### Unicode ‘ALT+’ code entry

Example: the 'delta' symbol, Δ, is encoded by Unicode in hexadecimal as 'U+0394'.

To insert Unicode symbols using their hexadecimal representations, hold the 'alt' key, press the '+' key on the numpad, and then type the hex code (which may contain 0-9 and a-f).

If this doesn't work at all, or you get the same character that you would if you had not hit ‘+’, do the following:

1.  hit 'windows key - r'; type 'regedit' and hit enter
2.  navigate through the tree to the following location: **HKEY_CURRENT_USER** / **Control Panel** / **Input Method**
3.  Right-click and select 'New: String Value'
4.  Name this new object 'EnableHexNumpad'
5.  Right-click and select 'modify'; set the value to '1' and hit 'ok'
6.  Now reboot the computer and try again!

[Updated advice for using Unicode in Microsoft Office](http://office.microsoft.com/en-us/project-help/insert-ascii-or-unicode-latin-based-symbols-and-characters-HA010167539.aspx).

Unicode hex codes can be found by a Google search, in the Word or Docs ‘Insert Special Character’ dialogs, or at the Unicode official website: <http://www.unicode.org/charts/>

Linux Unicode entry
-------------------

Two methods of Unicode hex code input have been reported to work in most programs:

1.  Press and release ‘ctrl-shift-u’, then type the Unicode hex code (described above) and hit ‘enter’.
2.  Press and hold ‘ctrl-shift’, then type ‘u’ followed by the Unicode hex code and release all keys.

Linux Compose key
-----------------

For diacritic marks and certain other common symbols, an additional input method is much more intuitive than using Unicode hex codes. Many Linux distributions incorporate a special key called the “compose” key. This key allows you to effectively “compose” the shapes of symbols on the keyboard by using it in sequence with other keys:

` [compose]  +  ‘  +  a = á`
``  [compose]  +  `  +  e = è ``
` [compose]  +  ,  +  c = ç`
` [compose]  +  =  +  e = €`

And so on. Most Linux systems don’t enable the Compose key by default, so often you’ll need to choose where to put it on your keyboard. The method of doing this may vary by Linux distribution, but in general it will be an option in your system preferences. For instance, in Ubuntu Linux 10.04, the standard way to configure the key is:

1.  Navigate to “System &gt;&gt; Preferences &gt;&gt; Keyboard”.
2.  Select the “Layouts” tab in the Keyboard Preferences interface.
3.  Select the “Options” button near the bottom of the Layouts tab.
4.  Select the “Compose key position” tree tab.
5.  Check one or more of the check boxes in the tree tab to choose the position of the Compose key.
6.  Click “Close” and then “Close” to save the configuration.

Many common Unicode characters can be produced easily using the compose key, and a list of common compose sequences can be found on the Wikipedia article: <http://en.wikipedia.org/wiki/Compose_key>.

Mac OSX
-------

from Wikipedia: <http://en.wikipedia.org/wiki/Unicode_input#In_Mac_OS>

In Mac OS 8.5 and later: one chooses the Unicode Hex Input keyboard layout: open the International preferences pane of Mac OS X's System Preferences, go to the Keyboard Menu tab, and enable the Unicode Hex Input checkbox.

Once activated: Holding down the Option key, one then types the four-digit hex Unicode code point and the equivalent character appears. One can then release the option key.

Particularly Useful Unicode Symbols
-----------------------------------

|                      |                      |                      |                      |
|----------------------|----------------------|----------------------|----------------------|
| | Unicode | Symbol |
 |---------|--------|
 | 2192    | →      |
 | 21CC    | ⇌      |
 | 21CB    | ⇋      |
 | 00B0    | °      |
 | 00B5    | µ      |
 | 2081-9  | ₁-₉    |
 | 2093    | ₓ      |
 | 00b9    | ¹      |
 | 00B2    | ²      |
 | 00B3    | ³      |
 | 2079    | ⁴-⁹    |
 | 2021    | ‡      |
 | 232C    | ⌬      |
 | 23E3    | ⏣      |
 | 2620    | ☠      |
 | 2622    | ☢      |
 | 2623    | ☣      |
 | 269B    | ⚛      |
 | 2697    | ⚗      |
 | 2234    | ∴      |  | | Unicode | Symbol |
                        |---------|--------|
                        | 00AF    | ¯      |
                        | 2206    | ∆      |
                        | 2248    | ≈      |
                        | 221A    | √      |
                        | 2211    | ∑      |
                        | 222B    | ∫      |
                        | 223F    | ∿      |
                        | 2260    | ≠      |
                        | 2264    | ≤      |
                        | 2265    | ≥      |
                        | 226A    | ≪      |
                        | 226B    | ≫      |
                        | 00B7    | ·      |
                        | 2605    | ★      |
                        | 2606    | ☆      |
                        | 00A7    | §      |
                        | 2014    | —      |
                        | 03B1    | α      |
                        | 03B2    | β      |
                        | 2019    | ’      |  | | Unicode | Symbol |
                                               |---------|--------|
                                               | 2022    | •      |
                                               | 2665    | ♥      |
                                               | 25D0    | ◐      |
                                               | 25E9    | ◩      |
                                               | 2639    | ☹      |
                                               | 26A0    | ⚠      |
                                               | 26A1    | ⚡      |
                                               | 2082    | ₂      |
                                               | 2093    | ₓ      |
                                               | 207A    | ⁺      |
                                               | 207B    | ⁻      |
                                               | 00B9    | ¹      |
                                               | 00E9    | é      |
                                               | 2122    | ™      |
                                               | 2020    | †      |
                                               | 00B5    | µ      |
                                               | 0394    | Δ      |
                                               | 03A9    | Ω      |
                                               | 03C0    | π      |
                                               | 2192    | →      |  | | Unicode | Symbol |
                                                                      |---------|--------|
                                                                      | 221E    | ∞      |
                                                                      | 2714    | ✔      |
                                                                      | 2718    | ✘      |
                                                                      | 2260    | ≠      |
                                                                      | 2265    | ≥      |  |

[Category:Software](/Category:Software "wikilink")