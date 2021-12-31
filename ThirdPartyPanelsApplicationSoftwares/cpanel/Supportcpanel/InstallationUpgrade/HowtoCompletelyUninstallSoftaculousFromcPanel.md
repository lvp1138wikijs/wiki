---
title: How to Completely Uninstall Softaculous From cPanel
description: 
published: true
date: 2021-12-31T18:00:01.245Z
tags: 
editor: markdown
dateCreated: 2021-12-31T18:00:01.245Z
---

# How to Completely Uninstall Softaculous From cPanel


If you follow Softaculous Uninstall Guide from their website to uninstall softaculous, you may find out there’s still something left behind or the softaculous link still shows in WHM under Plugins.

- This is uninstall guide from softaculous.com

```
/usr/local/cpanel/bin/unregister_cpanelplugin /usr/local/cpanel/whostmgr/docroot/cgi/softaculous/softaculous.cpanelplugin 
rm -rf /etc/cron.d/softaculous 
rm -rf /var/softaculous 
rm -rf /usr/local/cpanel/whostmgr/docroot/cgi/softaculous 
rm -rf /usr/local/cpanel/whostmgr/docroot/cgi/addon_softaculous.php 
rm -rf /usr/local/cpanel/base/frontend/x3/dynamicui/dynamicui_softicons.conf
```

- If you want to completely uninstall Softaculous, you need to execute following commands in SSH.

```
rm -f /usr/local/cpanel/whostmgr/docroot/cgi/addon_softaculous.cgi 
rm -f /usr/local/cpanel/base/frontend/x/cells/softaculous.html 
rm -f /usr/local/cpanel/base/frontend/x2/cells/softaculous.html 
rm -rf /usr/local/cpanel/base/frontend/x/softaculous 
rm -rf /usr/local/cpanel/base/frontend/x2/softaculous 
rm -rf /usr/local/cpanel/base/frontend/x3/softaculous 
rm -rf /usr/local/cpanel/base/frontend/x3mail/softaculous
```