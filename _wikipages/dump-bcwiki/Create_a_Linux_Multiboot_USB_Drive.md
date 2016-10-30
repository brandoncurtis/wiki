---
title: Create a Linux Multiboot USB Drive
permalink: /Create_a_Linux_Multiboot_USB_Drive/
---

This procedure will create a USB drive from which you can boot pretty much any Linux ISOs that you'd like.

Creating the Multiboot USB Drive
--------------------------------

Install the GRUB2 bootloader to the device:

`sudo` `apt-get` `install` `grub2` `sudo` `grub-install` `--force` `--no-floppy` `--root-directory=/media/USB_DRIVENAME` `/dev/sdx`

Or on Ubuntu 12.10+:

`sudo` `grub-install` `--force` `--no-floppy` `--root-directory=/media/USERNAME/USB_DRIVENAME` `/dev/sdx`

where X is the drive designation (sda, sdb, sdc... &etc).

Don't know the drive designation? Figure it out with `df` `-Th`.

Configuring the Multiboot USB Drive
-----------------------------------

Drop as many Linux ISOs as you would like to the root of the drive.

To add these ISOs to the boot selection list, customize the drive's grub.conf:

`nano` `/media/`<DRIVE_NAME>`/boot/grub/grub.cfg`

Example grub.conf Entries
-------------------------

### Header

    # This grub.cfg file was created by Brandon Curtis (brandon.curtis@gmail.com) on the AndHigherStill wiki

    set timeout=10
    set default=0

### Ubuntu 12.04.1

    menuentry "Ubuntu 12.04.1 x64 Desktop ISO - Live" --class ubuntu {
      set isoname="ubuntu-12.04.1-desktop-amd64.iso"
      set isofile="${isopath}/${isoname}"
      echo "Using ${isoname}..."
      loopback loop $isofile
      linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=${isofile} quiet splash
      initrd (loop)/casper/initrd.lz
    }

    menuentry "Ubuntu 12.04.1 x64 Desktop ISO - Install" --class ubuntu {
      set isoname="ubuntu-12.04.1-desktop-amd64.iso"
      set isofile="${isopath}/${isoname}"
      echo "Using ${isoname}..."
      loopback loop $isofile
      linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=${isofile} quiet splash only-ubiquity
      initrd (loop)/casper/initrd.lz
    }

### Ubuntu 12.04.2

    menuentry "Ubuntu 12.04.2 x64 Desktop ISO - Live" --class ubuntu {
      set isoname="ubuntu-12.04.2-desktop-amd64.iso"
      set isofile="${isopath}/${isoname}"
      echo "Using ${isoname}..."
      loopback loop $isofile
      linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=${isofile} quiet splash
      initrd (loop)/casper/initrd.lz
    }

    menuentry "Ubuntu 12.04.2 x64 Desktop ISO - Install" --class ubuntu {
      set isoname="ubuntu-12.04.2-desktop-amd64.iso"
      set isofile="${isopath}/${isoname}"
      echo "Using ${isoname}..."
      loopback loop $isofile
      linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=${isofile} quiet splash only-ubiquity
      initrd (loop)/casper/initrd.lz
    }

### Ubuntu 12.04.3

    menuentry "Ubuntu 12.04.3 x64 Desktop ISO - Live" --class ubuntu {
      set isoname="ubuntu-12.04.3-desktop-amd64.iso"
      set isofile="${isopath}/${isoname}"
      echo "Using ${isoname}..."
      loopback loop $isofile
      linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=${isofile} quiet splash
      initrd (loop)/casper/initrd.lz
    }

    menuentry "Ubuntu 12.04.3 x64 Desktop ISO - Install" --class ubuntu {
      set isoname="ubuntu-12.04.3-desktop-amd64.iso"
      set isofile="${isopath}/${isoname}"
      echo "Using ${isoname}..."
      loopback loop $isofile
      linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=${isofile} quiet splash only-ubiquity
      initrd (loop)/casper/initrd.lz
    }

### Ubuntu 12.04.4

    menuentry "Ubuntu 12.04.4 x64 Desktop ISO - Live" --class ubuntu {
      set isoname="ubuntu-12.04.4-dvd-amd64.iso"
      set isofile="${isopath}/${isoname}"
      echo "Using ${isoname}..."
      loopback loop $isofile
      linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=${isofile} quiet splash
      initrd (loop)/casper/initrd.lz
    }

    menuentry "Ubuntu 12.04.4 x64 Desktop ISO - Install" --class ubuntu {
      set isoname="ubuntu-12.04.4-dvd-amd64.iso"
      set isofile="${isopath}/${isoname}"
      echo "Using ${isoname}..."
      loopback loop $isofile
      linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=${isofile} quiet splash only-ubiquity
      initrd (loop)/casper/initrd.lz
    }

### Ubuntu 13.04

    menuentry "Ubuntu 13.04 x64 Desktop ISO - Live" --class ubuntu {
      set isoname="ubuntu-13.04-desktop-amd64.iso"
      set isofile="${isopath}/${isoname}"
      echo "Using ${isoname}..."
      loopback loop $isofile
      linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=${isofile} quiet splash
      initrd (loop)/casper/initrd.lz
    }

    menuentry "Ubuntu 13.04 x64 Desktop ISO - Install" --class ubuntu {
      set isoname="ubuntu-13.04-desktop-amd64.iso"
      set isofile="${isopath}/${isoname}"
      echo "Using ${isoname}..."
      loopback loop $isofile
      linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=${isofile} quiet splash only-ubiquity
      initrd (loop)/casper/initrd.lz
    }

### Ubuntu 14.04

    menuentry "Ubuntu 14.04 x64 Desktop ISO - Live" --class ubuntu {
      set isoname="ubuntu-14.04-desktop-amd64.iso"
      set isofile="${isopath}/${isoname}"
      echo "Using ${isoname}..."
      loopback loop $isofile
      linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=${isofile} quiet splash
      initrd (loop)/casper/initrd.lz
    }

    menuentry "Ubuntu 14.04 x64 Desktop ISO - Install" --class ubuntu {
      set isoname="ubuntu-14.04-desktop-amd64.iso"
      set isofile="${isopath}/${isoname}"
      echo "Using ${isoname}..."
      loopback loop $isofile
      linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=${isofile} quiet splash only-ubiquity
      initrd (loop)/casper/initrd.lz
    }

Example syslinux.cfg Entries
----------------------------

If you use a multiboot script such as [Multisystem](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/) to create a multiboot USB drive, you may have to customize your own syslinux.cfg file in the `multibootusb` folder.

### Ubuntu 16.04

    LABEL Ubuntu_1604_x64
    MENU LABEL Ubuntu 16.04 x64
    kernel /multibootusb/ubuntu-16.04-desktop-amd64/casper/vmlinuz.efi
    append initrd=/multibootusb/ubuntu-16.04-desktop-amd64/casper/initrd.lz live-media-path=/multibootusb/ubuntu-16.04-desktop-amd64/casper boot=live console-setup/layoutcode=it ignore_uuid boot=casper quiet splash --

[Category:Linux](/Category:Linux "wikilink")