---
title: How to retrieve Plesk admin password on Windows
description: 
published: true
date: 2021-07-18T03:23:46.675Z
tags: 
editor: markdown
dateCreated: 2021-07-18T03:23:46.675Z
---

# How to retrieve Plesk admin password on Windows

In order to set up a new password or retrieve the old one, you can use the plesksrvclient.exe utility located in the %plesk_bin% folder.

You can set up a new password by running the following command:


```
"%plesk_bin%\plesksrvclient" -set <new_password> true
```

You can also retrieve the current password by running this utility with:

```
"%plesk_bin%\plesksrvclient" -get
```

To retrieve the password in the command line, you can use -nogui option:

```
"%plesk_bin%\plesksrvclient" -get  -nogui > plesk_password.txt
```
After that, you can find the retrieved Plesk password in the plesk_password.txt file.


