---
title: Configuring Ubuntu 14.04 LTS
permalink: /Configuring_Ubuntu_14.04_LTS/
---

Install
-------

Wipe the disk; use LVM

Configure the software update settings

update all; restart

Proprietary Software
--------------------

-   ubuntu-restricted-extras
-   [Google Chrome](http://www.google.com/chrome)
-   [Mendeley](http://www.mendeley.com/download-mendeley-desktop/ubuntu/instructions/)
-   [Kingsoft Office](http://wps-community.org/)

Additional Configuration
------------------------

Note that [the dconf configuration system is slowly but surely replacing the old gconf configuration system](http://askubuntu.com/questions/91403/when-to-use-gconf-vs-dconf); dconf-editor and gsettings edit dconf, while gconftool2 edits gconf. If your configuration scripts currently use gconftool2, be prepared for them to break as more software is ported over to the dconf system!

### Unity Tweak Tool

use this tool to configure the number of workspaces.

### remove workspace switcher

via [AskUbuntu:](http://askubuntu.com/questions/38789/how-do-i-add-and-remove-the-workspace-switcher-launcher-from-the-unity-launcher)

-   gsettings get com.canonical.Unity.Launcher favorites
-   gsettings set com.canonical.Unity.Launcher favorites "\[...\]"

### Display date in Y-M-D (ISO) format

-   gsettings set com.canonical.indicator.datetime custom-time-format '%Y.%m.%d %T'
-   gsettings set com.canonical.indicator.datetime time-format 'custom'
-   gsettings set com.canonical.indicator.datetime show-week-numbers true

### Start the Week on a Monday

via: <http://askubuntu.com/questions/6016/how-to-set-monday-as-the-first-day-of-the-week-in-gnome-calendar-applet>

sudo nano /etc/default/locale

    LANG="en_US.UTF-8"
    LC_TIME="en_GB.UTF-8"
    LC_PAPER="en_US.UTF-8"
    LC_MEASUREMENT="en_GB.UTF-8"

### Default folder view

-   gsettings set org.gnome.nautilus.preferences default-folder-viewer 'list-view' (alt: 'icon-view')
-   gsettings set org.gnome.nautilus.preferences default-sort-order 'name' (alt: 'atime','type','size')

### Create 'bin' and 'repo' folders

-   mkdir ~/bin && chmod -R u+x ~/bin

### Create hotkeys

-   mkdir ~/repo

### Generate an SSH key

yes '' | ssh-keygen -N ''

### Adjust Swap Usage

Check current usage:

    cat /proc/sys/vm/swappiness

Change usage:

    sudo sysctl vm.swappiness=10
    sudo nano /etc/sysctl.conf
    # Decrease swap usage
    vm.swappiness=10

### Display hidden startup applications

sudo sed -i "s/NoDisplay=true/NoDisplay=false/g" /etc/xdg/autostart/\*.desktop

### Keyboard configuration

if your keyboard lacks media buttons, go to 'Sound and Media' and set 'volume up', 'volume down', and 'mute' to ctrl+alt+super+up, ctrl+alt+super+down, ctrl+alt+super+space respectively.

### Command Aliases

Add command aliases to the end of ~/.bashrc.

for instance, I add this to keep track of CPU throttling:

`alias` `cpuspeed="grep` `-E` `'^model` `name|^cpu` `MHz'` `/proc/cpuinfo"`

### Unity Search

Uninstall the Amazon lens, &etc.

`sudo` `apt-get` `purge` `unity-lens-shopping`

### Fixing Monitor Overscan or Underscan

-   [Overscanning picture problem using HDMI with Intel Graphics](http://askubuntu.com/questions/508358/overscanning-picture-problem-using-hdmi-with-intel-graphics)
-   [How to adjust HDMI Overscan on an Intel Ivy Bridge?](http://askubuntu.com/questions/248094/how-to-adjust-hdmi-overscan-on-an-intel-ivy-bridge)

### Logical Volume Manager (LVM)

[How can I resize an LVM partition?](http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume/489909#489909)

Boot from LiveCD, then install `system-config-lvm`:

    $ sudo add-apt-repository "deb http://archive.ubuntu.com/ubuntu $(lsb_release -sc) universe"
    $ sudo apt-get update
    $ sudo apt-get install system-config-lvm

Recommended software
--------------------

you definitely need these:

    unity-tweak-tool pinta pdfmod alarm-clock-applet pidgin libreoffice libreoffice-nlpsolver guake stellarium filezilla chromium-browser arduino inkscape ssh sshfs nmap traceroute apt-file hardinfo gsmartcontrol clementine git vlc vlc-plugin-fluidsynth fluid-soundfont-gs fluid-soundfont-gm wine

and these are good for working with different filesystems:

    gparted gpart xfsprogs reiserfsprogs reiser4progs kpartx jfsutils hfsutils hfsprogs davfs2

if you do math stuff, you may like these too:

    ipython ipython-notebook ipython-doc python-matplotlib python-matplotlib-doc gimp gimp-data-extras gimp-flegita gimp-gutenprint gimp-plugin-registry

Stuff I used to install that I don't install anymore:

    dconf-tools k3d openclipart-libreoffice videolan-doc gedit-plugins deluge deluged deluge-web gnome-shell gnome-panel xsane

-   Add SSH key to inventory and GitHub
-   Clone in desired Git repos
-   Install [Sage Math](/Sage_Math "wikilink")
-   Set the monitor turnoff and lock times
-   Log into the Ubuntu Software Center with your Ubuntu One credentials
-   Log into Google Chrome with your Google credentials
-   Add startup applications
-   Log into Mendeley
-   Install Comsol
-   Organize launcher items
-   Create other user accounts

### Playing DVDs

<http://howtoubuntu.org/how-to-play-a-dvd-in-ubuntu>

<https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs>

Other Configuration Guides
--------------------------

-   [Easy Linux Tips - Do this first in Ubuntu 14.04 LTS](https://sites.google.com/site/easylinuxtipsproject/first)

Other Configuration Guides
--------------------------

Getting AnyConnect-compatible openconnect VPN transport to appear in network-manager:

-   \[<http://tomtomtom.org/networkmanager-openconnect/>

FIXING UNUSABLE NETWORK-MANAGER-OPENCONNECT-PLUGIN ON XENIAL XERUS\]

-   [No more AnyConnect compatible vpn transport in Ubuntu 16.04](https://askubuntu.com/questions/760864/no-more-anyconnect-compatible-vpn-transport-in-ubuntu-16-04)

[Category:Linux](/Category:Linux "wikilink")