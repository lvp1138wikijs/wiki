---
title: Unable to create new account in cpanel
description: 
published: true
date: 2021-12-27T16:15:09.198Z
tags: 
editor: markdown
dateCreated: 2021-12-27T16:15:09.198Z
---

# Unable to create new account in cpanel


When you try to create account via WHM (WHM >> Create new account), you may come across the following message:

```
The /usr partition on this server is running out of disk space. WHM operation has been temporarily suspended to

prevent something bad from happening. Please ask your system admin to remove any files not in use on that partition.
```

If the "/usr" partition is full, clear it and it should resolve the issue. Sometimes even after clearing the space the issue persists. In that case you can execute the following commands to fix it.

```
/scripts/upcp --force

touch /var/cpanel/disablestatfs
/etc/init.d/cpanel restart
```

