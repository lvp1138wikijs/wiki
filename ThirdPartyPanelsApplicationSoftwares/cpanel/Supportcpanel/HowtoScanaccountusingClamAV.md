---
title: How to Scan account using ClamAV
description: 
published: true
date: 2021-12-27T20:01:56.818Z
tags: 
editor: markdown
dateCreated: 2021-12-27T20:01:56.818Z
---

# How to Scan account using ClamAV

You can scan your accounts using the following commands :

```
clamscan -ir /home/username -l clamscanreport
```

If you wish to scan your whole server then use the below given command :

```
clamscan -ir / -l clamscanreport
```

After clamscan is completed a new file will be created with name clamscanreport which will contain your clam scan report.

To remove virus infected file just add --remove=yes option at the end of the command

```
clamscan -ir /home/username -l clamscanreport --remove=yes
clamscan -ir / -l clamscanreport --remove=yes
```


