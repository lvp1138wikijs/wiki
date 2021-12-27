---
title: Related to PHP
description: 
published: true
date: 2021-12-27T18:55:00.181Z
tags: 
editor: markdown
dateCreated: 2021-12-27T18:55:00.181Z
---

# Related to PHP

**Upgrading PHP version to 5**

Before you upgrade the PHP version , make sure that you will either note or memorize the modules that were enabled in previous php version and once the upgrades done

you will have to enable those php modules again before it starts throwing out the error.

- Login  to the server SSH as root 
- Use /scripts/upcp – force
- this can take a while. 
- Use /script/easyapache

Once you used the above command , it will show the options screen ( You can do the php version upgrade from WHM easyapache too )
 
SELECT OPTION 7

- Select ―Php Module —>‖
- Uncheck current PHP version 
- Check latest version of PHP5
- Select ―Exit‖
- Select ―Exit‖ again
- Sit back and wait, it can take 10-60 minutes to complete