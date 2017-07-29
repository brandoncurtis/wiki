---
title: Configuring Ubuntu 16.04 LTS
permalink: "/Configuring_Ubuntu_16.04_LTS/"
---

Software Installation
---------------------

[Create and customize launcher icons by hand](http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand)

Create custom application launcher icons for the current user by creating <appname>`.desktop` files in `~/.local/share/applications/` and images for these icons in `~/.local/share/icons/`. For example, the contents of `.local/share/applications/trans-connect-d105.desktop`:

    [Desktop Entry]
    Encoding=UTF-8
    Version=1.0
    Type=Application
    Name=Torrents @D105
    Icon=bc-d105
    Exec=trans-connect-d105
    StartupNotify=false
    OnlyShowIn=Unity;
    X-UnityGenerated=true
    X-Desktop-File-Install-Version=0.22

This application is represented by `~/.local/share/icons/bc-d105.png` (note the lack of full path and file extension in the <appname>`.desktop` file) and when clicked, runs the script `trans-connect-d105` in the system $PATH (meaning, this script has executable permissions and is somewhere like <code>~/bin/

<script>
</code> so it can be executed in the terminal from any working directory just by typing the script's name, full or relative path needed). Add the application to your launcher by searching for them in the Unity dash and then dragging and dropping them to the launcher.

To install an application for all users, instead put <appname>`.desktop` in `~/usr/share/applications/` and images for these icons in `/usr/share/pixmaps/`.

### Apt Install

`sudo` `apt` `install` `unity-tweak-tool` `ppa-purge` `git` `gimp` `guake` `stellarium` `chromium-browser` `python-pip` `libfreetype6-dev` `libpng12-dev` `libffi-dev` `libssl-dev` `ant` `openjdk-8-jdk` `mdadm` `kate` `autokey-gtk` `pidgin`

### Personal Package Archives (PPAs)

Nothing currently! See 'Not Used' below.

### Free Downloads

-   [Bitcoin Daemon and Wallet](/Bitcoin,_Cryptocurrency,_and_Blockchains "wikilink")

Add Facebook Chat to Pidgin, [via webupd8](http://www.webupd8.org/2016/04/things-to-do-after-installing-ubuntu-1604-lts-xenial-xerus.html):

`"Facebook shut down their XMPP service in 2015 and because of this, Pidgin/libpurple no longer supports Facebook Chat. For those of you who want to use Facebook Chat in Pidgin, there's a new plugin which makes this possible, called purple-facebook."`

-   <https://github.com/dequis/purple-facebook>
-   <http://download.opensuse.org/repositories/home:/jgeboski/xUbuntu_16.04/amd64/>

### Non-Free Downloads

-   [Google Chrome - web browser](https://www.google.com/chrome/)
-   [Spotify - music streaming service](https://www.spotify.com/us/download/linux/)
-   [Dropbox - cloud-based file sync service](https://www.dropbox.com/install?os=lnx)
-   [Mendeley Desktop - literature management service](https://www.mendeley.com/download-mendeley-desktop/ubuntu/instructions/)

### From Source

The [latest stable version of the Arduino IDE in the repositories is 1.0.5](https://launchpad.net/ubuntu/xenial/+source/arduino); this is really old, so we can clone the Arduino source from Github and [build the newest stable version (v1.6.9) ourselves](https://github.com/arduino/Arduino/wiki/Building-Arduino):

`git` `clone` `git@github.com:/arduino/Arduino.git` `~/repo/arduino`

### Service Log-Ins

-   Google Accounts in Chrome
-   Firefox Sync
-   Github Authentication

Configuration Commands
----------------------

### Look and Feel

Change the number of workspaces with the Unity Tweak Tool or by editing these keys in the dconf database:

-   dconf write /org/compiz/profiles/unity/plugins/core/hsize 2
-   dconf write /org/compiz/profiles/unity/plugins/core/vsize 2

Note that these keys will NOT exist in a fresh install - they'll appear when you [turn on the workspace switcher in Unity Tweak Tool](http://askubuntu.com/questions/34572/how-can-i-reduce-or-increase-the-number-of-workspaces-in-unity). It is probably possible to active the workspace switcher plugin and create the keys from the terminal.

    gsettings set com.canonical.indicator.datetime custom-time-format '%Y.%m.%d %T'
    gsettings set com.canonical.indicator.datetime time-format 'custom'
    gsettings set com.canonical.indicator.datetime show-week-numbers true
    gsettings set org.gnome.nautilus.preferences default-folder-viewer 'list-view'
    gsettings set org.gnome.nautilus.preferences default-sort-order 'name'
    gsettings set com.canonical.Unity.Launcher launcher-position Bottom
    sudo sed -i "s/NoDisplay=true/NoDisplay=false/g" /etc/xdg/autostart/*.desktop
    sudo sysctl vm.swappiness=10

    sudo nano /etc/default/locale
      LANG="en_US.UTF-8"
      LC_TIME="en_GB.UTF-8"
      LC_PAPER="en_US.UTF-8"
      LC_MEASUREMENT="en_GB.UTF-8"

### Operating System Settings

    mkdir ~/repo

    ssh-keygen

    sudo nano /etc/sysctl.conf
      # Decrease swap usage
      vm.swappiness=10

    DOESN'T WORK:
    sudo apt purge unity-lens-shopping

    via: http://www.pcworld.com/article/2840401/ubuntus-unity-8-desktop-removes-the-amazon-search-spyware.html
    eliminated in Unity 8, but default is Unity 7

    via: http://www.omgubuntu.co.uk/2016/04/10-things-to-do-after-installing-ubuntu-16-04-lts
    online search is disabled by default in Unity 7

    via: https://wiki.ubuntu.com/Unity8Desktop
    Install Unity 8 preview with Mir desktop:
    sudo apt install unity8-desktop-session-mir

    more stuff via: http://www.omgubuntu.co.uk/2016/04/10-things-to-do-after-installing-ubuntu-16-04-lts

    Enable ‘Minimise on Click’
    gsettings set org.compiz.unityshell:/org/compiz/profiles/unity/plugins/unityshell/ launcher-minimize-window true

    Move The Unity Launcher
    gsettings set com.canonical.Unity.Launcher launcher-position Bottom
    ----
    https://bitbucket.org/cffi/cffi/issues/38/sudo-pip-install-cffi-fails-under-ubuntu

### Virtual Environments for Python Development

preparing a virtualenv containing Julia in Jupyter: <https://docs.google.com/document/d/13mw6SAP94zFa_jtcaoYqHKwppNv5V3bb1fvpwBQM7Z0/edit#>

Setting up virtualenvwrapper:

    pip install virtualenvwrapper
    nano ~/.bashrc
     # setup for virtualenvwrapper
     export WORKON_HOME=$HOME/.virtualenvs
     export PATH=$PATH:$HOME/.local/bin
     source /home/brandon/.local/bin/virtualenvwrapper.sh

    mkvirtualenv graveslab
    pip install requests[security]
    pip install numpy scipy matplotlib jupyter

RAID Configuration
------------------

-   [mdadm Cheat Sheet](http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/)
-   [Linux RAID Setup](https://raid.wiki.kernel.org/index.php/RAID_setup)

To get an existing RAID1 array working after adding its configuration information to /dev/mdadm/mdadm.conf, I first needed to remove dmraid with `sudo` `apt` `remove` `dmraid` and reboot; /dev/md0 then appeared, and I could mount this by configuring /etc/fstab.

Uninstalling Stuff
------------------

If you install something from the repositories and decide you don't want it, it's easy to completely uninstall with:

`sudo` `apt-get` `remove` <package-name> `&&` `sudo` `apt-get` `autoremove`

If you install something from a Personal Package Archive (PPA), manual removal takes a couple steps. Use \`ppa-purge\` to automate these steps:

`sudo` `apt-get` `install` `ppa-purge` `sudo` `ppa-purge` <ppa-creator>`/`<ppa-name>

Stuff I Don't Use
-----------------

Apparently you can [integrate Google Drive with the Nautilus file manager via GVfs and Gnome Online Accounts](http://www.webupd8.org/2016/03/use-gnome-318-google-drive-integration.html), but I haven't played with it.

Pidgin is up-to-date in the repos, so there's no need to install from a PPA or compile from source:

    Xenial repos: https://launchpad.net/ubuntu/xenial/+source/pidgin
    1:2.10.12-0ubuntu5
    Uploaded:
    2016-03-10

    https://www.pidgin.im/
    2.10.12

VLC is already the newest stable version, so this doesn't do anything:

    newest stable version of VLC:
    https://launchpad.net/~videolan/+archive/ubuntu/stable-daily

    sudo add-apt-repository ppa:videolan/stable-daily
    was: 2.2.2-5
    now: 2.2.2-5 (so this didn't do anything)

Libreoffice is already the newest stable version, so this doesn't do anything:

    newest stable version of libreoffice:
    https://launchpad.net/~libreoffice/+archive/ubuntu/ppa

    sudo add-apt-repository ppa:libreoffice/ppa
    was: 1:5.1.2-0ubuntu1
    now: 1:5.1.2-0ubuntu1 (so this didn't do anything)

Gimp is already the newest stable version, so this doesn't do anything:

    Newest stable version of GIMP:
    https://launchpad.net/~otto-kesselgulasch/+archive/ubuntu/gimp

    sudo add-apt-repository ppa:otto-kesselgulasch/gimp
    sudo apt-get update
    sudo apt install gimp
    was: 2.8.16-1ubuntu1
    now: 2.8.16-1ubuntu1 (so this didn't do anything)

    References:
    http://askubuntu.com/questions/134035/how-do-i-get-the-latest-gimp-version-available
    http://ubuntuhandbook.org/index.php/2015/11/how-to-install-gimp-2-8-16-in-ubuntu-16-04-15-10-14-04/
    http://tipsonubuntu.com/2015/04/04/instal-latest-gimp-image-editor/

I prefer the default theme over the ARC theme, so I didn't use it:

    add the ARC GTK theme:
    http://www.omgubuntu.co.uk/2015/06/arc-gtk-theme

    sudo sh -c "echo 'deb http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04/ /' >> /etc/apt/sources.list.d/arc-theme.list"
    wget http://download.opensuse.org/repositories/home:Horst3180/xUbuntu_16.04/Release.key
    sudo apt-key add - < Release.key
    sudo apt-get update
    sudo apt install arc-theme

    install the ARC theme for Firefox:
    http://www.omgubuntu.co.uk/2015/08/an-official-arc-theme-for-firefox-is-now-available

References
----------

Bugs
----

Fixing network-manager-openconnect in Ubuntu 16.04:

-   <http://askubuntu.com/questions/760864/no-more-anyconnect-compatible-vpn-transport-in-ubuntu-16-04>
-   <http://tomtomtom.org/networkmanager-openconnect/>
-   <https://bugs.launchpad.net/ubuntu/+source/network-manager-openconnect/+bug/1571300>
-   <https://launchpad.net/ubuntu/+source/network-manager-openconnect>
-   <https://launchpad.net/ubuntu/xenial/+source/network-manager-openconnect>
-   <https://launchpad.net/~tomtomtom/+archive/ubuntu/network-manager-openconnect-xenial>

How to install just one package from xenial-proposed?

-   <http://askubuntu.com/questions/187471/is-it-possible-to-install-a-specific-package-from-proposed-repos>
-   <http://ubuntuguide.net/enable-proposed-pre-released-updates-ubuntu-12-04>
-   <https://help.ubuntu.com/community/PinningHowto>

Removing a package's build dependencies:

-   <http://askubuntu.com/questions/180504/how-can-i-remove-all-build-dependencies-for-a-particular-package>
-   you should be using pbuilder to build packages anyway!
