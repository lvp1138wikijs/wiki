---
title: SiteBuilder icon is missing from cPanel 11(Theme x3)
description: 
published: true
date: 2021-12-27T16:11:47.889Z
tags: 
editor: markdown
dateCreated: 2021-12-27T16:11:47.889Z
---

# SiteBuilder icon is missing from cPanel 11(Theme x3)


cPanel Version 11 uses a different procedure for adding icons to the control panel. If the site builder icon is missing, you need to create a "plug-in" based on this new architecture. The steps to install this new plugin the server are as follows,

1) Login to the server as root.

2) Then execute the following commands

```
# cd /usr/local/sitezen/prd/cpanelscripts
# wget support.sitemagix.com/download/sitezen.cpanelplugin
# wget support.sitemagix.com/download/cpanel_updateskins11.sh
# perl cpanel_updateskins11.sh
```

Now you can see the Sitebuilder icon in the cpanel with theme x3.

