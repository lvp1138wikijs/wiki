---
title: How to enable viewing HTML content in Horde
description: 
published: true
date: 2021-12-23T19:34:50.316Z
tags: 
editor: markdown
dateCreated: 2021-12-23T19:34:50.316Z
---

# How to enable viewing HTML content in Horde


By default it is not possible for us to view the emails in HTML format using Horde webmail interface. All the html content will be displayed at the top of the page and will be requested to download.

In order to fix this issue, you have to enable "Inline HTML message viewing" in the server.

For enabling "Inline HTML message viewing" in the server, please do the following steps:

```
1. Goto the horde imp configuration folder at /usr/local/cpanel/base/horde/imp/config

2. Edit the file mime_drivers.php using your favorite editor.

3. Change the line "$mime_drivers['imp']['plain']['inline'] = false;" to "$mime_drivers['imp']['plain']['inline'] = true;"

 4. Restart the cpanel service in the server.
 ```
 
 Now you will be able to view the html content using Horde webmail interface.

