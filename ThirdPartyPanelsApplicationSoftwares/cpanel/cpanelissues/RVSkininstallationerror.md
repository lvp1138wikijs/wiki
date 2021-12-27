---
title: RVSkin installation error
description: 
published: true
date: 2021-12-27T16:10:33.422Z
tags: 
editor: markdown
dateCreated: 2021-12-27T16:10:33.422Z
---

# RVSkin installation error


During the installation of Rvskin Manager, when creating the settings in the Features List if you are getting the following error even if the disk size is not full.

```
"Sorry,your disk space usage is full."
```

The issue might be due to the incorrect permissions or attributes of files/folders in '/home', which cannot write file in your home directory.

You need to set the ownership of "rvadmin" properly.  That is, /home/rvadmin.

```
# chown rvadmin.rvadmin rvadmin
```

This should fix the issue. Now you can proceed the installation :)

