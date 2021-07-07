---
title: Installing Softaculous in Plesk Linux
description: 
published: true
date: 2021-07-07T23:58:14.535Z
tags: 
editor: markdown
dateCreated: 2021-07-07T23:58:14.535Z
---

# Installing Softaculous in Plesk Linux


Softaculous is the leading Auto Installer for cPanel, Plesk, DirectAdmin, etc..

**Requirements**

- A server with Plesk Linux
- If you have a firewall, then please allow access to all packages from *.softaculous.com

```
Note : Please allow access to the following domains to your firewall as these are the mirrors used to download the script packages.

s2.softaculous.com
s4.softaculous.com
```

## Installing Softaculous

```
Note: Before starting the installation make sure ionCube Loaders are enabled. Otherwise you will not be able to Install Softaculous.
```

- Now SSH to your server as root and run following commands:

```
wget -N http://files.softaculous.com/install.sh
chmod 755 install.sh
./install.sh
```

The Installer will start showing the Installation Processes and when done will indicate the same.


```
NOTE: Scripts will be downloaded during this process. The Download Activity will also be shown on the screen.
```
That's it the installation of Softaculous is completed. Now login to plesk control panel as admin. You can see Softaculous Auto Installer under Links to Additional Services from plesk left side menu.
