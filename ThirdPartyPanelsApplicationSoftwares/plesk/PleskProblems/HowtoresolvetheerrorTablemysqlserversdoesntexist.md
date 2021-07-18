---
title: How to resolve the error "Table ‘mysql.servers’ doesn’t exist"
description: 
published: true
date: 2021-07-18T03:20:58.650Z
tags: 
editor: markdown
dateCreated: 2021-07-18T03:20:58.650Z
---

# How to resolve the error "Table ‘mysql.servers’ doesn’t exist"

After plesk upgrade  or  with newly installed plesk , if you are not able to set the passwords for the new database users or not able to do any kind of activity with the database users and mysql error log shows the following error:

```
[ERROR] Can’t open and lock privilege tables: Table ‘mysql.servers’ doesn’t exist
```

In order to resolve the above error, please do the following steps:

1.Login to mysql with admin privileges as shown in below.

```
#mysql -uadmin -p`cat /etc/psa/.psa.shadow` -h localhost
```

2. Go into mysql database.

```
mysql> use mysql;
```

3. create server table.

```
mysql> CREATE TABLE `servers` (
`Server_name` char(64) NOT NULL,
`Host` char(64) NOT NULL,
`Db` char(64) NOT NULL,
`Username` char(64) NOT NULL,
`Password` char(64) NOT NULL,
`Port` int(4) DEFAULT NULL,
`Socket` char(64) DEFAULT NULL,
`Wrapper` char(64) NOT NULL,
`Owner` char(64) NOT NULL,
PRIMARY KEY (`Server_name`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8
COMMENT=’MySQL Foreign Servers table’;
```

4. ‘Server’ table is created.

You should be able to operate the required database now.

