---
title: systemd-networkd
permalink: p/systemd-networkd
layout: wikipage
category: software
featured: true
---

## DHCP

`sudo nano /etc/systemd/network/wired.network`

```
[Match]
Name=enp*

[Network]
DHCP=ipv4
```

`sudo systemctl start systemd-networkd`

`sudo systemctl enable systemd-networkd`

`sudo systemctl status systemd-networkd`

Current DHCP leases are stored in `/run/systemd/netif/leases/*`

## systemd-resolved

A DNS resolution service.  I don't think you need this in most situations.

## wpa_supplicant

You need this if you need to do some sort of authentication on your network.

`sudo nano /lib/systemd/system/wpa_supplicant-wired@.service`

```
[Unit]
Description=WPA supplicant daemon (interface- and wired driver-specific version)
Requires=sys-subsystem-net-devices-%i.device
After=sys-subsystem-net-devices-%i.device
Before=network.target
Wants=network.target

# NetworkManager users will probably want the dbus version instead.

[Service]
Type=simple
ExecStart=/usr/bin/wpa_supplicant -c/etc/wpa_supplicant/wpa_supplicant-wired-%I.conf -Dwired -i%I

[Install]
Alias=multi-user.target.wants/wpa_supplicant-wired@%i.service
```

`sudo systemctl start wpa_supplicant-wired-enp1s0.service`

`sudo systemctl enable wpa_supplicant-wired-enp1s0.service`

----

`sudo nano /lib/systemd/system/wpa_supplicant@.service`

```
[Unit]
Description=WPA supplicant daemon (interface-specific version)
BindsTo=sys-subsystem-net-devices-%i.device
After=sys-subsystem-net-devices-%i.device
Wants=network.target
Before=network.target

[Service]
Type=oneshot
RemainAfterExit=yes
#ExecStart=/sbin/ip 1 set %i up
ExecStart=/sbin/wpa_supplicant -B -i %i -c /etc/wpa_supplicant/wpa_supplicant-%i.conf
#ExecStart=/sbin/dhclient %i

[Install]
Alias=multi-user.target.wants/wpa_supplicant@%i.service
#WantedBy=multi-user.target
```

----

`sudo nano /lib/systemd/system/wpa_supplicant-wext@.service`


```
[Unit]
Description=WPA supplicant daemon (interface-specific version)
BindsTo=sys-subsystem-net-devices-%i.device
After=sys-subsystem-net-devices-%i.device
Wants=network.target
Before=network.target

[Service]
Type=oneshot
RemainAfterExit=yes
ExecStart=/sbin/ip l set %i up
ExecStart=/sbin/wpa_supplicant -i %i -D wext -c /etc/wpa_supplicant/wpa_supplicant-%i.conf
#ExecStart=/sbin/dhclient %i
ExecStop=/sbin/ip l set %i down

[Install]
Alias=multi-user.target.wants/wpa_supplicant@%i.service
#WantedBy=multi-user.target
```

`sudo nano /etc/wpa_supplicant/wpa_supplicant-wlp3s3.conf`

```
ctrl_interface=/run/wpa_supplicant

network={
  ssid="openwireless.org"
  key_mgmt=NONE
}
```

`sudo systemctl start wpa_supplicant-wlp3s3.service`

`sudo systemctl enable wpa_supplicant-wlp3s3.service`


## dhclient

A DHCP client.  You don't need this if you're using `systemd-networkd`.


## dhcpcd

`dhcpcd` is a network service used as the default in Raspbian builds (as of 2017-06).  A GUI is provided by `dhcpcd-ui`.  It looks nice but does NOT have support for wpa2-enterprise networks, which sucks.

+ https://aur.archlinux.org/packages/dhcpcd-ui/
+ https://roy.marples.name/projects/dhcpcd-ui
+

## References

+ https://wiki.archlinux.org/index.php/systemd
+ https://wiki.ubuntuusers.de/systemd/networkd/
+ https://wiki.archlinux.org/index.php/Systemd-networkd
+ https://www.freedesktop.org/software/systemd/man/systemd.network.html
+ https://github.com/systemd/systemd/
+ https://wiki.archlinux.org/index.php/WPA_supplicant
+ https://w1.fi/cvs.html
+ [How does systemd, wpa_supplicant, and dhcpcd work together?](https://bbs.archlinux.org/viewtopic.php?id=152627)
+ [systemd-networkd, wpa_supplicant and multiple USB Wifi adapters](https://bbs.archlinux.org/viewtopic.php?id=192095)
+ [wpa_supplicant@.service fails to start](https://bbs.archlinux.org/viewtopic.php?id=170353)
+ [Can't get systemd-networkd + wpa_supplicant to work](https://bbs.archlinux.org/viewtopic.php?id=200759)
+ https://en.wikipedia.org/wiki/Wpa_supplicant
+ [dhcpcd vs /etc/network/interfaces](https://raspberrypi.stackexchange.com/questions/39785/dhcpcd-vs-etc-network-interfaces)
+ [not getting dns from dhcp due to systemd-resolved](https://bbs.archlinux.org/viewtopic.php?id=198995)
+ [Switching to systemd-networkd](https://www.joachim-breitner.de/blog/664-Switching_to_systemd-networkd)
+
