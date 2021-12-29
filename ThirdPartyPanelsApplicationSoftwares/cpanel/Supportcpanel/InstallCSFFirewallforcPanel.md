---
title: Install CSF Firewall for cPanel
description: 
published: true
date: 2021-12-29T19:54:35.827Z
tags: 
editor: markdown
dateCreated: 2021-12-29T19:54:35.827Z
---

# Install CSF Firewall for cPanel

CSF firewall commonly known as Configserver Security and Firewall has become one of the popular firewall not just because of its easy of use it also provides a cpanel interface and can be easily installed and tuned by any novice users. If you are running cpanel without firewall then CSF firewall is very much recommended, considering the security aspects of your server.

**Installation Steps**

1. Download the package and untar it

```
cd /usr/src
wget http://www.configserver.com/free/csf.tgz
tar -zxf csf.tar.gz
```

2. Run the Install script.

```
sh csf/install.sh
```

Thats it! wait until the script ends!

3. Remove APF or IPTables Firewall
- If you have any existing IP tables firewall remove them using uninstall scripts located at /etc/csf. In this case i was running APF firewall and BFD in my server so i have to remove it.

```
sh /etc/csf/remove_apf_bfd.sh
```

4. Start the Firewall in Testing Mode
- Start the firewall with the following command.

```
csf -s
// start the firewall
csf -r
// restart the firewall
csf -f
// flush the rules or stop the firewall.
```
Thats all! Now restart the firewall. 

5. Specify which ports you want to allow

- It is very important to check the firewall on which ports to open and close all remaining port numbers. Open the /etc/csf/csf.conf and edit the following line with port numbers

```
# Allow incoming TCP ports
TCP_IN = "20,21,22,25,53,80,110,143,443,465,953,993,995,2077,2078,2082,2083,2087"
# Allow outgoing TCP ports
TCP_OUT = "20,21,22,25,37,43,53,80,110,113,443,587,873,953,2087,2089,2703"
# Allow incoming UDP ports
UDP_IN = "20,21,53,953"
# Allow outgoing UDP ports
# To allow outgoing traceroute add 33434:33523 to this list
UDP_OUT = "20,21,53,113,123,873,953,6277"
```

6. Disable the Testing Mode and Start the Firewall

- Remember by default the firewall is running in testing mode. You might want to disable the firewall running in testing mode.

```
vi /etc/csf/csf.conf
 
//Look for the first line and set testing mode to "0"
TESTING = "0"
 
//Now restart the firewall!
csf -r
```


**In cPanel**


If you have successfully installed the CSF firewall, then you will find this CSF Security & Firewall option within cpanel WHM at the bottom of the menu. Just click on the link and you can also edit the firewall settings inside Cpanel, which is very easy to do.

**Config Files**


- /etc/csf/csf.conf ⇒ CSF Firewall configuration file
- /etc/csf/csf.allow ⇒ Config file to allow IPs
- /etc/csf/csf.deny ⇒ Config file to deny IPs
- /etc/csf/ ⇒ Alert files with TXT extension are stored within this directory


**Final Steps**

1. Check the status of firewall inside cpanel
1. Harden the firewall security by performing the system security check. To do this go to cPanel/WHM > CSF Firewall & Security > Check System Security. There it will list WARNINGS based on your server.


> Note: Mr Peter had adviced *not* to suggest or install CSF for any customer on cpanel. if customer want csf then he can use it himself, but we do not suggest it" We will use only simple iptable rules on the cpanel
{.is-info}

 
