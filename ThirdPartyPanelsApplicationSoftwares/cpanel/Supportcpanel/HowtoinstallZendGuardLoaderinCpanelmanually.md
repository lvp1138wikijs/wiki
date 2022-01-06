---
title: How to install ZendGuard Loader in Cpanel manually
description: 
published: true
date: 2022-01-06T02:37:56.452Z
tags: 
editor: markdown
dateCreated: 2022-01-06T02:37:56.452Z
---

# How to install ZendGuard Loader in Cpanel manually


In order to install ZendGuard Loader in Cpanel server, please do the following steps:

1. Login to the server as root
1. Download the loaders

```
wget http://downloads.zend.com/guard/5.5....23-i386.tar.gz
```

3. Extract It and copy the file to the extension folder

```
tar -zxvf ZendGuardLoader-php-5.3-linux-glibc23-i386.tar.gz
cp ZendGuardLoader-php-5.3-linux-glibc23-i386/php-5.3.x/ZendGuardLoader.so /usr/local/lib/php/extensions/no-debug-non-zts-20090626/
```

4. Edit the file /usr/local/lib/php.ini using vi editor as follows

