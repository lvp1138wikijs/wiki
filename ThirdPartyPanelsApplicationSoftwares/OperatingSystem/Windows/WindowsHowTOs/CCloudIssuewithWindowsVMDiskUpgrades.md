---
title: CCloud: Issue with Windows VM Disk Upgrades
description: 
published: true
date: 2021-05-16T05:01:15.820Z
tags: 
editor: markdown
dateCreated: 2021-05-16T05:01:15.820Z
---

**Issue**: **Colossus customer has upgraded the disk space from client portal and showing that it was done successfully. But it is not reflecting in the server side**.

For an example

The customer has upgraded the disk drive from 25 Gb to 50 through the client portal. It didn't show any error.

In the server side the C: drive partition space from My computer it is still showing as 25 GB. But the Disk management utility is showing the correct space 50 GB space on C: drive. The actual space is not reflected on partition C:.

Then do the following steps.

Open Command prompt, start >> Command Prompt.

Then run the following commands

```
C:\Users\Administrator>diskpart
Microsoft DiskPart version 6.1.7601
Copyright (C) 1999-2008 Microsoft Corporation.
On computer: EjEm403rV
DISKPART> list volume
  Volume ###  Ltr  Label        Fs     Type        Size Status     Info
  ----------  ---  -----------  -----  ----------  ------- ---------  --------
  Volume 0     D                       DVD-ROM         0 B  No Media
  Volume 1     C                NTFS   Partition     49 GB Healthy    System
 
DISKPART> select volume 1
Volume 1 is the selected volume.
 
DISKPART> extend filesystem
DiskPart successfully extended the file system on the volume.
 
DISKPART> exit
Leaving DiskPart...
 
C:\Users\Administrator>
```

Now recheck check the disk space of partition C: and confirm.

