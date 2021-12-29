---
title: How to Install Softaculous on VPS or Dedicated Server with cPanel/WHM
description: 
published: true
date: 2021-12-29T19:38:44.557Z
tags: 
editor: markdown
dateCreated: 2021-12-29T19:38:44.557Z
---

# How to Install Softaculous on VPS or Dedicated Server with cPanel/WHM


**Installation via cPanel/WHM**

Note: Before starting the installation make sure ionCube Loaders are enabled. For that go to WHM and click on Tweak Settings. Please make sure that the Ioncube loader is selected for the backend copy of PHP. Now SSH to your server and enter following commands:

```
cd /usr/local/cpanel/whostmgr/docroot/cgi 
wget -N http://www.softaculous.com/ins/addon_softaculous.php
chmod 755 addon_softaculous.php
```

Now go to: WHM > Plugins (Add-Ons on older versions than 11) > Softaculous - Instant Installs. A new  webpage will open if the installation was successful.

You can also install it from Command Line Installation Option using the following commands without having to visit cPanel/WHM.

```
cd /usr/local/cpanel/whostmgr/docroot/cgi 
wget -N http://www.softaculous.com/ins/addon_softaculous.php
chmod 755 addon_softaculous.php
/usr/local/cpanel/3rdparty/bin/php /usr/local/cpanel/whostmgr/docroot/cgi/addon_softaculous.php
```

