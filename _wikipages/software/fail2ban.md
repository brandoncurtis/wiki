---
layout: default
category: software
title: Hardening with `fail2ban`
permalink: p/fail2ban
---

+ [How to Prevent SSH Brute Force Attacks with Fail2Ban on Debian 7](https://www.unixmen.com/how-to-prevent-ssh-brute-force-attacks-with-fail2ban-on-debian-7/)
+ [Installing Fail2ban on Debian 8.0](https://www.upcloud.com/support/installing-fail2ban-on-debian-8-0/)
+ [Using `fail2ban` to secure your server](https://www.linode.com/docs/security/using-fail2ban-for-security)

```
sudo apt install fail2ban
sudo nano /etc/fail2ban/jail.d/defaults-debian.conf
sudo fail2ban-client status ssh
sudo fail2ban-client start
sudo fail2ban-client reload
sudo fail2ban-client stop
```

/etc/fail2ban/action.d/ contains a big list of potential actions

/etc/fail2ban/filter.d/sshd.conf contains preconfigured service filters

/etc/fail2ban/jail.d/defaults-debian.conf contains the default Debian configuration, which enables the fail2ban service for sshd


/etc/fail2ban/jail.local set bantime:

```
[DEFAULT]
bantime = 3600
```

Check out the fail2ban action log: `tail -f /var/log/fail2ban.log`

To remove fail2ban entries from the iptables:

iptables -D f2b-sshd 1
