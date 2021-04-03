---
title: Questions on Snapshots 
description: 
published: true
date: 2021-04-03T12:48:57.192Z
tags: 
editor: markdown
dateCreated: 2021-04-03T12:48:57.192Z
---

1) Is the ccloud snapshots are compressed?

Backup for Linux VM are compressed, but Windows backups are not compressed, mainly they are ntfs clone of the disk.

 

2) How the backup space is billed ?

Backup space will be billed at $0.10/mo per 1GB

 

3) Is backup auto-rotated ?

Yes, client portal will keep only 7 days old backup and will be auto-rotated on regular basis.

 

4) How to remove corrupted snapshot ?

All corrupted snapshots will be deleted after 7 days of its creation. No manual removal option is available now.