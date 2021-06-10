---
title: Install IonCube Loader in Ubuntu
description: 
published: true
date: 2021-06-10T18:23:07.503Z
tags: 
editor: markdown
dateCreated: 2021-06-10T17:33:24.552Z
---

# IonCube : Ubuntu

IonCube protects software written using the PHP programming language from being viewed, changed, and run on unlicensed computers.

Here the steps for installing IonCube Loader in Ubuntu

1. Download ionCube loaders

```
sudo wget http://downloads.ioncube.com/loader_downloads/ioncube_loaders_lin_x86.tar.gz
```

2. Extract

```
sudo tar zxvf ioncube_loaders_lin_x86.tar.gz
```

3. Move to a permanent location

```
sudo mv ioncube /usr/local/
```

4. Add reference to your php.ini file (vi /etc/php5/apache2/php.ini)

```
zend_extension = /usr/local/ioncube/ioncube_loader_lin_5.2.so
```

5. Restart apache

```
/etc/init.d/apache2 restart
```

> There are a few versions of the loader in the tar archive. Use the one that matches your PHP version.
{.is-info}



