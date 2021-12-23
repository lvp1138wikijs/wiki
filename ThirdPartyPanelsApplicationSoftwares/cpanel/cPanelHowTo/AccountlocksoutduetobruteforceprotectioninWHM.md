---
title: Account locks out due to brute force protection in WHM
description: 
published: true
date: 2021-12-23T19:10:47.952Z
tags: 
editor: markdown
dateCreated: 2021-12-23T19:10:47.952Z
---

# Account locks out due to brute force protection in WHM


> The brute force protection on cPanel-powerd web host is provided by cPHulk, which prevents malicious forces from trying to access the server’s services by guessing the login password for that service. When an account on the system has experienced too many failed login attempts, the particular account will automatically been “protected” by forbidding further login attempts, including all-important root account. cPHulk Brute Force Protection will also block out an IP address which has been detected to send too many unauthorized logon attempts.
{.is-info}


When WHM locks out an user account, especially “root”, the best way is to wait for 10 minutes to see if the account will be unlocked. If the locks persists, webmaster and administrator who still can remote login via SSH to the server as root can manually remove the lockouts via following steps:

1. Type mysql at console to access MySQL client.

2. At MySQL client prompt, enter the following commands one after one.

```
mysql> use cphulkd;

mysql> BACKUP TABLE `brutes` TO ‘/path/to/backup/directory’;

mysql> BACKUP TABLE `logins` TO ‘/path/to/backup/directory’;
```

**Note**: Above command will backup the brutes table, the main table used by cPHulk to record locked accounts and denied IP addresses.

```
mysql> DELETE FROM `brutes`;
mysql> DELETE FROM `logins`;
```

**Note**: Above commands will remove all blocked IP addresses and locked accounts from the system, enabling full access again. If you’re familiar with SQL statements, it’s possible to use WHERE clause to specify logins or IP address that you want to remove only.

Exit MySQL client using the below command:

```
mysql> quit;
```

To avoid future blockage or lock out, it’s recommended to add own IP address as Trusted Hosts List whitelist in cPHulk Brute Force Protection. To do so please refer here .



