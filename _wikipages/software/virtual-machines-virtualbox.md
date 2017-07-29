---
title: Virtual Machines in VirtualBox
permalink: p/virtualbox
layout: default
category: software
featured: true
---

Ubuntu 16.04
------------

Video acceleration will have some... issues... when you first create an Ubuntu 16.04 virtual machine in VirtualBox. Follow these steps to fix them: <https://blogs.oracle.com/fatbloke/entry/3d_acceleration_with_ubuntu_guests>

It may also help to fire up the 'additional drivers' GUI in the Ubuntu guest system and manually select the proprietary acceleration drivers.

Test your video configuration with `/usr/lib/nux/unity_support_test` `-p`; if you see some stuff about being software-rendered and not supporting Unity 3D, you're not there yet!

Once it's set up, an Ubuntu guest VM running on an Ubuntu host in VirtualBox should be buttery smooth!

### Clean VM for Development and Troubleshooting

    gsettings set com.canonical.indicator.datetime custom-time-format '%Y.%m.%d %T'
    gsettings set com.canonical.indicator.datetime time-format 'custom'
    gsettings set com.canonical.indicator.datetime show-week-numbers true
    gsettings set org.gnome.nautilus.preferences default-folder-viewer 'list-view'
    gsettings set org.gnome.nautilus.preferences default-sort-order 'name'
    gsettings set com.canonical.Unity.Launcher launcher-position Bottom
    sudo sed -i "s/NoDisplay=true/NoDisplay=false/g" /etc/xdg/
    sudo sysctl vm.swappiness=10
    sudo nano /etc/default/locale
    mkdir ~/repo

    ssh-keygen
    gedit .ssh/id_rsa.pub
    sudo apt install python-pip
    pip install --upgrade pip
    pip install virtualenvwrapper
    nano ~/.bashrc
        # setup for virtualenvwrapper
        export WORKON_HOME=$HOME/.virtualenvs
        export PATH=$PATH:$HOME/.local/bin
        source /home/brandon/.local/bin/virtualenvwrapper.sh
    source ~/.bashrc

Now it's ready to go! Make linked clones of this VM for short-term development work; it only takes a second to create them and they don't take up much space!

### Make Your VM Servers Accessible

By default, VirtualBox configures your guest operating systems to use NAT; this provides access to the Internet, but it is not possible to connect to the guest OS from the host OS or the wider network.

If you want to run a server on your guest OS, say an Apache webserver or a Jupyter notebook server, you'll need to make the guest OS accessible:

1.  Shut down your VM
2.  Under settings &gt; networking, change the network type to 'bridged adapter'
3.  Restart your VM and check your server's accessibility!

Some web services, like Jupyter Notebooks, are configured by default to only be accessible from localhost. To access these services without reconfiguration, install an SSH server on the guest OS and SSH into it from the host OS with local port forwarding.

1.  on the guest: `sudo` `apt` `install` `openssh-server`
2.  on the guest: `ifconfig`; note your inet address.
3.  on the host: `ssh` <guest-inet-addr> `-L` <host-port>`:localhost:`<guest-server-port>

For instance, to connect to a Jupyter Notebook server running on the Guest OS at 169.168.1.10 on the default port 8888:

1.  on the guest: start the Jupyter server with `jupyter` `notebook`
2.  on the host: `ssh` `169.168.1.10` `-L` `11000:localhost:8888`
3.  on the host: open a web browser and point it at localhost:11000, and there's your Jupyter interface!
