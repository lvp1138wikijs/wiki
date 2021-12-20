---
title: Perl: DBI module to access mysql database
description: 
published: true
date: 2021-12-20T20:55:03.201Z
tags: 
editor: markdown
dateCreated: 2021-12-20T20:55:03.201Z
---

To access mysql databases using Perl DBI follow the steps:

Login to your linux server using SSH.

At the beginning of your perl script use the line:

```
use DBI;
```

Type the following connection string to connect to your database::

```
$connection=DBI-
>connect("DBI:mysql:database=$database;host=$host:port=3306",
$username, $password);
```

