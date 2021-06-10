---
title: Install Mcrypt-PHP
description: 
published: true
date: 2021-06-10T18:26:08.142Z
tags: 
editor: markdown
dateCreated: 2021-06-10T17:38:59.828Z
---

# MCrypt for PHP : Ubuntu

> Install mCrypt for PHP5 on Ubuntu Linux system
{.is-info}

mCrypt is an encryption program used on Linux systems.

To install mCrypt for PHP5 on Ubuntu Linux system:

- sudo apt-get install php5-mcrypt

Then restart Apache with:

- sudo /etc/init.d/apache2 restart

# MCrypt for PHP : CentOS

>  Install mCrypt for PHP5 on CentOS Linux system
{.is-info}

Install mCrypt using Yum

- yum –enablerepo=webtatic install php-mcrypt
- yum –enablerepo=webtatic install php-mbstring

Then restart the apache service

- service httpd restart



