---
title: How to repair a SUSPECT database in MSSQL 2008
description: 
published: true
date: 2021-04-27T15:09:12.297Z
tags: 
editor: markdown
dateCreated: 2021-04-27T15:09:12.297Z
---

In order to repair a suspect database in MSSQL 2008, please do the following SQL queries:

**Note**: there is a possibility this will lead to data loss, so copy the mdf and ldf files of the database first by taking DB offline, copying the two files, and bringing it back online. Then run the following queries in SQL to try to get the database out of SUSPECT mode:

```
ALTER DATABASE yourDBname SET EMERGENCY
DBCC checkdb(’yourDBname’)
ALTER DATABASE yourDBname SET SINGLE_USER WITH ROLLBACK IMMEDIATE
DBCC CheckDB (’yourDBname’, REPAIR_ALLOW_DATA_LOSS)
ALTER DATABASE yourDBname SET MULTI_USER
```

