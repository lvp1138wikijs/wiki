---
title: Install JavaScript Object Notation-JSON
description: 
published: true
date: 2021-06-10T18:24:07.619Z
tags: 
editor: markdown
dateCreated: 2021-06-10T17:35:45.044Z
---

# Install JavaScript Object Notation-JSON

JavaScript Object Notation

> Requirements
> If you're not seeing the json functions on 5.2.0 or newer, make sure php wasn't compiled with –disable-json
{.is-info}

**Installation steps on CentOs**

1. yum install php-devel
1. yum install php-pear
1. yum install gcc
1. pear install pecl/json

Once its installed, a new folder will be created in /etc/php.d

- cd /etc/php.d
- echo “extension=json.so” > json.ini
- service httpd restart

After that phpinfo() would output


> json support enabled
> 
> json version 1.2.1
{.is-warning}
