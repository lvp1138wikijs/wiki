---
title: How to check cPanel Ports are Open
description: 
published: true
date: 2021-12-27T19:50:19.615Z
tags: 
editor: markdown
dateCreated: 2021-12-27T19:50:19.615Z
---

# How to check cPanel Ports are Open

**From Windows do the following:**

```
Open Start >> Click Run
Type cmd
Type telnet youripaddress 2083
Type telnet youripaddress 2082
```

**From Linux do the following**:

```
Start your Linux/Mac OS console terminal
Type telnet your_ipaddress 2083
Type telnet your_ipaddress 2082
```

If the port is not blocked the results should look like the following one.

```
Connected to servername.com.
Escape character is '^]'.
```

