---
title: How to Disable Direct Root login
description: 
published: true
date: 2021-12-27T19:54:39.449Z
tags: 
editor: markdown
dateCreated: 2021-12-27T19:54:39.449Z
---

# How to Disable Direct Root login

**Disable Root Login for SSH**

**STEP 1: Create a user and add it to the wheel group**

SSH into your server as root and follow the below commands to create a user.

```
 groupadd test
 useradd test -gtest
 passwd test
```

Replace test with any username.

**STEP 2: Add user to wheel group**


You can add the user at the end of the ‘group’ file.

- For CPanel Servers, do the following.
- Log into your WHM and click on “Manage Wheel Group Users”.
- Select the user (Here it is “test”) and click ‘Add to group’.

- Before disable the root access, check if the user can login and su – to gain root privileges.
- SSH into your server and login as ‘test’
- Password : write your test user password
- Then run command

su –
password: enter root password here


**STEP 3: Disable Direct Root Login**

1. Open SSH configuration file sshd_config

```
vi /etc/ssh/sshd_config
```

2. Find the line

```
Protocol 2, 1
```

3. Uncomment it (Remove #) and change it to look like

```
Protocol 2
```

4. Next, find the line

```
PermitRootLogin yes
```
5. Uncomment it (Remove #) and make it look like PermitRootLogin no

6. Save the file.

7. Then restart SSH service

```
/etc/init.d/sshd restart
```

Now, no one will be able to login to root with out first logging in as ‘test’ and ‘su -’ to root

