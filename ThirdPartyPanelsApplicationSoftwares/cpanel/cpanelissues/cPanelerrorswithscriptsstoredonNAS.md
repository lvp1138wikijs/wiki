---
title: cPanel errors with scripts stored on NAS.
description: 
published: true
date: 2021-12-27T15:00:13.545Z
tags: 
editor: markdown
dateCreated: 2021-12-27T15:00:13.545Z
---

# cPanel errors with scripts stored on NAS.


An easy to use file server that combines Windows-compatible network file sharing with an advanced web based file manager and includes support for SMB, SFTP and rsync file transfer protocols. The server is configured to allow server users to manage files in private or public storage. Based on Samba and AjaXplorer.

When using a cron script executed by cPanel that is stored on the Limestone NAS, you will need to modify the mount command to include the uid and gid of the cPanel user which is running the bash script.


For example

```
mount -t cifs -o username=cli####,password=yourPassword,uid=yourCpanelUid,gid=yourCpanelGid, \
file_mode=0755,dir_mode=0755 //74.63.205.205/nas.nas.cli#### /mnt/nasCpanelUser
```

