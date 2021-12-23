---
title: Tomcat
description: 
published: true
date: 2021-12-23T14:19:38.746Z
tags: 
editor: markdown
dateCreated: 2021-12-23T14:19:38.746Z
---

# Tomcat

Tomcat is a server that is used to run java applications.

Here are the steps to install and run the tomcat server in linux.

1. First download and extract the apache-tomcat distribution using the wget command.

2. Next verify the MD5 checksum.

```
$md5sum apache-tomcat-[#].tar.gz
```

3. Next untar the contents from its package.

```
$ tar xvzf apache-tomcat-[#].tar.gz
```

4. Next set the required environment variable.

```
$ vi ~/.bashrc
export JAVA_HOME=/usr/lib/path/to/java
export CATALINA_HOME=/path/to/tomcat
```

where JAVA-HOME and CATALINA_HOME are two variables. CATALINA_HOME is the tomcat directory.

Then move on to start tomcat:

```
$ $CATALINA_HOME/bin/startup.sh
```

Next check if tomcat runs on the correct port:

```
$ ps -ef | grep java | grep 8080
```

If the catalina process is shown then tomcat installation is successful.


## Howto Uninstall Tomcat

First move to the stoptomcat folder

```
  cd /usr/sbin/stoptomcat

```

Next execute the following commands to remove the files that  control tomcat

```
rm -f /usr/sbin/starttomcat
rm -f /usr/sbin/startomcat
rm -f /usr/sbin/stoptomcat
```

Also remove all the mod_jk lines from the Apache httpd.conf file


