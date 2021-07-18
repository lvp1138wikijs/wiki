---
title: How To solve error Errcode: 13
description: 
published: true
date: 2021-07-18T04:53:19.827Z
tags: 
editor: markdown
dateCreated: 2021-07-18T04:53:19.827Z
---

# How To solve error Errcode: 13

Reference ticket: JGQ-377-88463

If a customer gets an error similar to 

```
1 - Can't create/write to file '/tmp/#sql_db3_0.MYI' (Errcode: 13)
describe categories status
```

Please check whether the permission of /tmp is 777.

If not please correct it to 777.