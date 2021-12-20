---
title: installing jboss on linux
description: 
published: true
date: 2021-12-20T20:42:54.644Z
tags: 
editor: markdown
dateCreated: 2021-12-20T20:42:54.644Z
---

1. First install Java and set the environment variables

2. Next create user jboss
```
useradd jboss
```

3. Next download and untar the jboss package from the internet using wget

```
tar -xvxf jboss-5.1.0.GA-jdk6.zip
```

4. Move it to a directory
```
mv jboss-5.1.0.GA /usr/local/
```

5. Change the ownership of teh folder to jboss
```
chown -R jboss:jboss /usr/local/jboss-5.1.0.GA
```
6. Next set environment variables for jboss in a new file

```
 touch /etc/profile.d/jboss
 chmod +x /etc/profile.d/jboss
 ```
7. Edit teh file and make appropriate entries

```
 #vi /etc/profile.d/jboss 
 #***** Set Env Variables for Jboss
 JBOSS_HOME=/usr/local/jboss-5.1.0.GA
 export JBOSS_HOME
 export PATH=$JBOSS_HOME/bin:$PATH
 export LAUNCH_JBOSS_IN_BACKGROUND=1
```

7. Next start the jboss server:
```
/sbin/service jboss start
```
jboss can be accessed from the browser on port 8080