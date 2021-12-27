---
title: Fix permission on all users in home directory script
description: 
published: true
date: 2021-12-27T15:25:26.889Z
tags: 
editor: markdown
dateCreated: 2021-12-27T15:25:26.889Z
---

# Fix permission on all users in home directory script


You can execute the below script to fix the permission on all users in home directory.

```
for i in $(ls /var/cpanel/users/)
do
USER=$i

chown -R $USER.$USER $USER
chown $USER.nobody $USER/public_html
chown $USER.nobody $USER/.htpasswds
chown $USER.mail $USER/etc
```

