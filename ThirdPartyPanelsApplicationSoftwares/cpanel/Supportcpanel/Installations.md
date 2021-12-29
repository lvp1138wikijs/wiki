---
title: Installations
description: 
published: true
date: 2021-12-29T19:42:43.002Z
tags: 
editor: markdown
dateCreated: 2021-12-29T19:42:43.002Z
---

# Installations


## How to Install Perl Modules

Perl Modules can be obtained from the CPAN (Comprehensive Perl Archive Network) at http://search.cpan.org

The easiest way to install Perl modules on Unix is to use the CPAN module.

shell> perl -MCPAN -e shell
 cpan> install DBI
 cpan> install DBD::mysql

**DBD::mysql is the Perl5 Database Interface driver  for the MySQL database**

To find a particular module, use the i command, followed by an expression that you want to search for

cpan> i /Time/



CPAN.pm will go out to the CPAN mirrror that you selected, download the list of modules, and tell you which ones match the search word

To install a module, just  type

cpan> install Time::CTime

CPAN.pm takes care of the whole process. It downloads the compressed file, unpacks it, builds it, and installs it all for you, unless there is a problem with the installation process. If there are other modules on which this modulerelies, it will also download and install those.


## How to install Eaccelerator

eAccelerator is a free open-source PHP accelerator, optimizer, and dynamic content cache. It increases the performance of PHP scripts by caching them in their compiled state, so that the overhead of compiling is almost completely eliminated. It also optimizes scripts to speed up their execution. eAccelerator typically reduces serverload and increases the speed of your PHP code by 1-10 times

1) Make sure PHP runs as DSO Apache module. For this purpose log into your cPanel server WHM and go to 'Configure PHP and SuExec'. There make sure that the PHP 5 Handler is set to dso.

2) Now log in as root by ssh and issue the following command

/scripts/phpextensionmgr install EAccelerator

## How to install Round cube

Before you start Installation remove the previous traces of Roundcube in the server

Use the below commands , by logging into the server with root

- cd /usr/local/cpanel/base
- rm -rf roundcube*
- mysql
- mysql>drop database roundcube;

Before starting the installation, make sure that you know the root password of Mysql

**Now use the below procedure**

cd /usr/local/cpanel/base

wget  http://easynews.dl.sourceforge.net/sourceforge/roundcubemail/roundcubemail-0.1beta2.1.tar.gz ( check for latest version )

tar -zxvf roundcubemail-0.1beta2.1.tar.gz ( change the file name accordingly to the Version )

mv -f roundcubemail-0.1beta2 roundcube

cd roundcube

chmod -R 777 temp

chmod -R 777 logs

**Now Create the database**

mysql -u root -p

mysql>CREATE DATABASE roundcube;

mysql>use roundcube;

mysql>source  SQL/mysql.initial.sql;

mysql>quit



**Now Add the configuration as below**

cd config

mv db.inc.php.dist db.inc.php

mv m ain.inc.php.dist main.inc.php

**Now Edit the configuration Files using your text editor edit db.inc.php**

 

  Find:
$rcmail_config*’db_dsnw’+ =  ‘mysql://roundcube:pass@localhost/roundcubemail’;
 Replace with:
$rcmail_config*’db_dsnw’+ =  ‘mysql://root:rootpass@localhost/roundcube’;
#vi main.inc.php


**Replace the corresponding root password**

Find:
$rcmail_config*’default_host’+ = ”;
Replace with:
$rcmail_config*’default_host’+ = ‘localhost’;
Configure cPanel to show roundcube in the theme. X theme(default) only


## How to reinstall horde

To reinstall Horde, preserving the existing database, you can use the following:

/usr/local/cpanel/bin/update-horde  – force


## How to Install RVSkins

RVSkin is an awesome skin for cPanel, the installation is pretty straight-forward, and is done via SSH, RVSkin is a multilingual, multi-theme advanced skin management software for cPanel server.Root access is required.The license for this skin needs to purchased.

mkdir /root/rvadmin

1) cd /root/rvadmin
2) wget http://download.rvglobalsoft.com/download.php/download/rvskin-auto/saveto/rvauto.tar.bz2bunzip2 -d rvauto.tar.bz2
3) tar -xvf rvauto.tarperl /root/rvadmin/auto_rvskin.pl
4) You can now login to WHM (as root) and navigate to RVSkin Manager, listed under Plugins in the left-handnavigation.

