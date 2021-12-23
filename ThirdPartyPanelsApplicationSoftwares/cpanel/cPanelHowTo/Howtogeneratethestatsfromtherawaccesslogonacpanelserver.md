---
title: How to generate the stats from the raw access log on a cpanel server
description: 
published: true
date: 2021-12-23T19:54:20.297Z
tags: 
editor: markdown
dateCreated: 2021-12-23T19:54:20.297Z
---

# How to generate the stats from the raw access log on a cpanel server


To generate the stats from the raw access log, you can follow the steps given below. Daily raw access log should be uploaded to the server on which it should be restored in gzip format.

1) Extract the all the access log from the gzip file into a directory.

```
cd /home/username/logs/

gunzip access*.gz
```

2) Now merge all the logs into a single file so that we can update it.

```
cat access* >> domainname.com

```

Replace domainname.com with the actual domainname

3) Replace the actual access log for the domain with the merged file. 

```
cp domainname.com /usr/local/apache/domlogs/domainname.com
```

4) Now update the stats for the domain

```
/scripts/runweblogs username
```

Replace username with the actual username

Now you can login to the cpanel and verify the stats.

NB: Please note that following these steps will erase all the current stats on the server. Please try it only after updating the customer or incase of site migration from a non-cpanel server.