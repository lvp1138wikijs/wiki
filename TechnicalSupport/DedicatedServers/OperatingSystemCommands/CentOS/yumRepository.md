---
title: Enable Yum Repositories
description: 
published: true
date: 2021-12-23T13:35:14.790Z
tags: yum repositories
editor: markdown
dateCreated: 2021-12-23T13:35:14.790Z
---

# Yum Repositories
##### CentOS 7
###### EPEL

> yum install epel-release
{.is-info}

###### PHP 5.5 & 5.6: 

> rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
{.is-info}

##### CentOS 6
###### EPEL

> rpm -ivh http://download.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm ; yum update

###### PHP 5.5 & 5.6

`rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-6.rpm`


**Enable Repo remi.repo for php 5.5 & 5.6
Go to /etc/yum.repos.d and open remi.repo and change enabled=0 to enabled=1 in both remi and remi-php56**


[remi]

> name=Les RPM de remi pour Enterprise Linux 6 - $basearch
> #baseurl=http://rpms.famillecollet.com/enterprise/6/remi/$basearch/
> mirrorlist=http://rpms.famillecollet.com/enterprise/6/remi/mirror
> enabled=1
> gpgcheck=1
> gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-remi
{.is-info}



[remi-php56]

> name=Les RPM de remi de PHP 5.6 pour Enterprise Linux 6 - $basearch
> #baseurl=http://rpms.famillecollet.com/enterprise/6/php56/$basearch/
> mirrorlist=http://rpms.famillecollet.com/enterprise/6/php56/mirror
{.is-info}

**#WARNING: If you enable this repository, you must also enable "remi"**
> enabled=1
> gpgcheck=1
> gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-remi
{.is-info}

 