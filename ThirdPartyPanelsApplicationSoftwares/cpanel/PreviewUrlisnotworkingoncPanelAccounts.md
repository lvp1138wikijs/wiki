---
title: Preview Url is not working on cPanel Accounts
description: 
published: true
date: 2021-12-27T16:51:50.731Z
tags: 
editor: markdown
dateCreated: 2021-12-27T16:51:50.731Z
---

# Preview Url is not working on cPanel Accounts


First check if mod_ruid2 is enabled on the server.

If yes, then disable mod_ruid2 via EasyApache4 UI in cPanel

Now enable mod_userdir from WHM

1.Login to WHM
(Home >> Security Center >> Apache mod_userdir Tweak)
See if mod_userdir Protection is enabled. If box is ticked, it means you won't be able to access your site using http://ip/~user

Make sure to provide exception for user 'nobody'

2. Please change the PHP handler to SUphp
(Home >> Service Configuration >> Configure PHP and SuExec)

3. If suPHP handler is not present, recompile EasyApache .

https://documentation.cpanel.net/display/EA/Apache+Module%3A+SuPHP