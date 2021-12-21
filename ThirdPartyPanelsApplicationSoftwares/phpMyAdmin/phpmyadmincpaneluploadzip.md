---
title: phpmyadmin-cpanel:upload zip
description: 
published: true
date: 2021-12-21T17:47:57.371Z
tags: 
editor: markdown
dateCreated: 2021-12-21T17:47:57.371Z
---

# phpmyadmin-cpanel:upload zip

- Login to your cpanel server through ssh
- Then edit the file:
 /var/cpanel/easy/apache/profile/makecpphp.profile.yaml
- Look for the line:
Cpanel::Easy::PHP5::Zip: 0
- Replace it with
 Cpanel::Easy::PHP5::Zip: 1
- Save the file and quit.
- Run the command /scripts/makecpphp
- You can now upload files to phpmyadmin in the zip format