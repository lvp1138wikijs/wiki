---
title: Installing/Upgrading Python in cpanel
description: 
published: true
date: 2021-12-29T20:54:20.118Z
tags: 
editor: markdown
dateCreated: 2021-12-29T20:54:20.118Z
---

# Installing/Upgrading Python in cpanel

Cpanel by default use python 2.4 and it is not recommended to upgrade since it may break mailmin which use python to run.

However different version of python can be installed and use separately.

```
Download required version of python from
http://www.python.org/ftp/python/
```

```
# cd /usr/local/src/
# wget  http://www.python.org/ftp/python/2.7/Python-2.7.tgz
# tar -xvzf Python-2.7.tgz
# cd Python-2.7/
# ./configure --prefix=/usr/local/python27 --with-threads --enable-shared
# make
# make install
# ln -s /usr/local/python27/bin/python /usr/bin/python2.7
# echo '/usr/local/python27/lib'>> /etc/ld.so.conf.d/opt-python27.conf
# ldconfig
```

```
Confirm Installation

root@vps [~]# python2.7 -V

Python 2.7
```

At this point, stop and tell above path to customer to use python 2.7

**However if customer want to integrate python 2.7 with cpanel, which is ofcourse not recommended, then you can go following**

```
nano -w /var/cpanel/cpanel.config
Find, python=/usr/local/bin/python2.4
change it to
python=python=/usr/local/bin/python2.7
```

Now reinstall Mailman

```
# /scripts/reinstallmailman
```