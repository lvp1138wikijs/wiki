---
title: Adding MySQL Instance to the Policy
description: 
published: true
date: 2021-04-15T19:48:14.863Z
tags: 
editor: markdown
dateCreated: 2021-04-15T19:48:14.863Z
---

Allow remote connections to mysql and add a separate user rather then using root user.

```
GRANT ALL PRIVILEGES ON *.* TO r1soft@'72.18.207.240' IDENTIFIED BY 'set-some-password';
GRANT ALL PRIVILEGES ON *.* TO r1soft@'127.0.0.1' IDENTIFIED BY 'set-some-password';
GRANT ALL PRIVILEGES ON *.* TO r1soft@'localhost' IDENTIFIED BY 'set-some-password';
```

Change "set-some-password" with your desired password.

http://wiki.r1soft.com/display/CDP3/Allowing+Remote+Connections+to+MySQL+Instance

 

After that follow

http://wiki.r1soft.com/display/CDP3/Adding+MySQL+Instance+to+the+Policy