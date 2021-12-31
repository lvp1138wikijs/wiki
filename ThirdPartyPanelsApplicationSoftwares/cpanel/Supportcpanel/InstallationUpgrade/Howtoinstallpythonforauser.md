---
title: How to install python for a user
description: 
published: true
date: 2021-12-31T18:03:32.995Z
tags: 
editor: markdown
dateCreated: 2021-12-31T18:03:32.995Z
---

# How to install python for a user


In order to install Python for a particular user, please do the following steps:

1.Log into server as user via SSH

2.Download Python package of required version from : http://www.python.org/getit/releases/

```
# wget http://www.python.org/ftp/python/2.6.6/Python-2.6.6.tgz
```

3.Unstar it using the below command

```
# tar -xvf Python-2.6.6.tgz
# cd Python-2.6.6
```

4.Configure and Install Python for user :

```
#./configure --prefix=/home/user_name/Python-2.6.6

# make

# make install
```

5.Python Binary for the user will be : /home/user_name/Python-2.6.6/bin/python and to check version:

```
# /home/user_name/Python-2.6.6/bin/python --version
```

