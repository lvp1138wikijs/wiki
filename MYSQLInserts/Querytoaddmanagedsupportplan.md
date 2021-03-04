---
title: Query for support plan in Colossuscloud VM
description: 
published: true
date: 2021-03-04T03:11:15.832Z
tags: 
editor: markdown
dateCreated: 2021-03-04T03:11:15.832Z
---

## QUERY TO ADD MANAGED SUPPORT PLAN

```
insert into cloudtrack_packages values ("","username","mg-supplan3","69.00","m","yyyy-mm-dd 00:00:00","yyyy-mm-dd");

Eg:- insert into cloudtrack_packages values ("","ludovicl","mg-supplan3","69.00","m","2017-10-15 00:00:00","2017-10-15");
```


## QUERY TO DELETE MANAGED SUPPORT PLAN FROM ACCOUNT

```
delete from cloudtrack_packages where sc_package = "mg-supplan3" and sc_username = "username";
```


