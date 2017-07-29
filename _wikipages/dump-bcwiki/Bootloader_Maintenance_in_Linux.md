---
title: Bootloader Maintenance in Linux
permalink: "/Bootloader_Maintenance_in_Linux/"
---

Background
----------

Linux uses the GRand Universal Bootloader (GRUB) to configure how the operating system is launched when the computer is turned on. The newest version, found in most all modern Linux distributions, is GRUB2. In order to function correctly, the bootloader needs to know the location of several important Linux components:

1.  vmlinuz ([wiki](http://en.wikipedia.org/wiki/vmlinux)) - this is a compressed image of the Linux kernel itself.
2.  initrd.img ([wiki](http://en.wikipedia.org/wiki/Initrd)) - this is the initial ramdrive that is used to make preparations before root is mounted.
3.  prefix - the path to the folder containing the bootloader configuration information.
4.  root - the drive partition containing the Linux root filesystem.

GRUB keeps track of these important locations through a set of system variables; from the GRUB interface, the ‘set’ command can be issued without arguments to display the values of these variables, and with arguments to change their values.

In rare instances, a hard drive reconfiguration, filesystem damage, or drive partition table modifications could cause GRUB to ‘lose track’ of the locations of the above components, resulting in a boot failure. GRUB2 allows straightforward recovery from boot failure by placing the user at a ‘grub rescue console. This guide covers how to use the GRUB rescue console to repair the bootloader and allow the system to boot.

GRUB2
-----

General documentation is available here: <https://help.ubuntu.com/community/Grub2>

GRUB2 rescue details: <https://help.ubuntu.com/community/Grub2/Troubleshooting>

Grub Rescue
-----------

From the grub-rescue prompt, issue the following commands.

Locate the bootloader configuration folder with:

<code>

    ls (hd0,X)/boot/grub

</code>

with X=(0 to 6) until this command returns a list of files that includes grub.cfg.

Once you know which value of X is correct (i.e. what partition number Linux is installed on), issue commands to set the bootloader's path variables. Assuming Linux is on partition 5 (X=5):

<code>

    set prefix=(hd0,5)/boot/grub
    set root=(hd0,5)
    insmod normal
    normal
    set linux /vmlinuz root=/dev/sda5 ro
    set /initrd.img
    boot

</code>

Once you’ve successfully entered Linux, automatically update grub.cfg by running:

<code>

    sudo update-grub

</code>

You should be good to go!

Reinstalling the Bootloader
---------------------------

    Boot from the USB drive and 'try without installing'.
    Open a terminal by hitting ctrl-alt-t. You can enter and run commands here.
    Determine which partition you have installed Linux, using the Terminal or the ‘Disk Utility’ program
        list information about all filesystems by running 'df -Th'.
    Mount the partition on which you have installed Linux:
        run: 'sudo mount /dev/sdXY /mnt', where sdXY is your Linux partition
    Reinstall the GRand Unified Bootloader (GRUB):
        run: 'sudo grub-install --root-directory=/mnt /dev/sdX'
        where sdX is the DRIVE with the Linux partition on it
    Now, unmount the Linux partition:
        run: 'sudo umount /mnt'
    Reboot.
        sudo reboot now

Glossary
--------

df - This command shows information about the file systems on the computer.

For more information, run ‘df --help’. options:

-   -T 'print-type' - lists the type of each filesystem (ntfs, ext4, etc)
-   -h 'human-readable' - cleans up the output of this command

[Category:Linux](/Category:Linux "wikilink")