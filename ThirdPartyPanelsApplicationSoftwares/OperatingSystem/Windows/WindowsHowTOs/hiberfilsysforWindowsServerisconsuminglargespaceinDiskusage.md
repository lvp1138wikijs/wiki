---
title: hiberfil.sys for Windows Server is consuming large space in Disk usage.
description: 
published: true
date: 2021-05-16T05:08:57.136Z
tags: 
editor: markdown
dateCreated: 2021-05-16T05:08:57.136Z
---

> While checking a disk space issue with Windows servers, the disk usage shows more that the usual usage and upon checking further with different disk checker tools, we can certainly see that the file "hiberfil.sys" which is dependent for the hibernation settings is consuming a large space in the disk usage. 
{.is-info}

**So What is hiberfil.sys Anyway**?

Windows has two power management modes that you can choose from: one is Sleep Mode, which keeps the PC running in a low power state so you can almost instantly get back to what you were working on. The other is Hibernate mode, which completely writes the memory out to the hard drive, and then powers the PC down entirely, so you can even take the battery out, put it back in, start back up, and be right back where you were.

Hibernate mode uses the hiberfil.sys file to store the the current state (memory) of the PC, and since it’s managed by Windows, you can’t delete the file

> **Note**: We don't use the hibernation mode for our Windows servers and so disabling the same is important for providing more free disk space for Cx. 
{.is-warning}

## Disable Hibernate (and Delete hiberfil.sys) in Windows servers

You’ll need to open an administrator mode command prompt by right-clicking on the command prompt in the start menu, and then choosing Run as Administrator. Once you’re there, type in the following command:

```
powercfg -h off
```

You should immediately notice that the Hibernate option is gone from the Shut down menu.You’ll also notice that the file is gone and there by providing more disk space.