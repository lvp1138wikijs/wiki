---
title: Install LiteSpeed and PHP on CentOS
description: 
published: true
date: 2021-12-28T13:56:40.724Z
tags: litespeed and php
editor: markdown
dateCreated: 2021-12-28T13:51:11.746Z
---

# Install LiteSpeed and PHP on CentOS

After you set-up the alecka server then install LiteSpeed webserver and compile PHP with LiteSpeed. Apache is not using as webserver is Alecka. It is just for internal use. So apache is running on different port than 80.

We are going to install LiteSpeed Standared Free Version. It is 32bit version. We can install it on 64 bit OS. Just follow the steps 

##### Pre-installation Steps

Install the required tools. Just run the following commands


**Required Tools**

> yum -y groupinstall 'Development Tools'
> yum -y install libpng-devel
> yum -y install bzip2 bzip2-devel bzip2-libs
> yum -y install libcurl-devel
> yum -y install libjpeg-devel
> yum -y install libXpm-devel
> yum -y install freetype-devel
> yum -y install libc-client-devel
> yum -y install openldap-devel
> yum -y install libxml2 libxml2-devel
> yum -y install openssl-devel
> yum -y install libmcrypt-devel
> yum -y install libxslt-devel
> yum -y install curl-devel
 
> ln -s /usr/bin/stunnel /var/serverchameleon/stunnel/sbin/stunnel
> ln -s /usr/lib64/libXpm.so /usr/lib/libXpm.so
> ln -s /usr/lib64/libc-client.so /usr/lib/libc-client.so
> ln -s /usr/lib64/libldap.so /usr/lib/libldap.so
> ln -s /usr/lib64/liblber-2.4.so.2 /usr/lib/liblber-2.4.so.2
> ln -s /usr/lib64/liblber.so  /usr/lib/liblber.so
> 

**Download the LiteSpeed source from their website using wget and install it**

> wget https://www.litespeedtech.com/packages/5.0/lsws-5.0.17-std-i386-linux.tar.gz
>  
> tar -zxvf lsws*
> cd lsws-5.0.17
> ./install.sh
 
 
 - It will ask for the necessary configuration values of LiteSpeed. Do the following 
 
 - Change the default litespeed installation directory (/usr/local/lsws) to - /var/serverchameleon/lsws
- Change the default litespeed web port (8088) to - 80
- Set Install PHP (Yes) to - No  (We will compile it later through teh GUI interface)


Upon successful installation, the following message is displayed.

**LiteSpeed Web Server started successfully! Have fun!**

Update the firewall rules

**Firewall**
> iptables -I INPUT -p tcp --dport 80 -j ACCEPT
> iptables -I INPUT -p tcp --dport 7080 -j ACCEPT
> service iptables save

**Start/Restart/Stop the LiteSpeed Webserver**

#### ***lswsctrl***

> /var/serverchameleon/lsws/bin/lswsctrl start
> /var/serverchameleon/lsws/bin/lswsctrl restart
> /var/serverchameleon/lsws/bin/lswsctrl stop

#### Compile PHP from LiteSpeed Admin GUI 
 - Login to the LiteSpeed Admin Panel - http://serverIPaddress:7080/login.php
 - Go Actions >> Select Compile PHP
 - Select the PHP version from the list and click on Next.
 - Change the configure Parameter value to the following
 
**PHP Parameters**

> --with-xsl --enable-mbstring --with-mysql-sock=/var/lib/mysql/mysql.sock --with-mysql --with-imap-ssl --with-imap --with-openssl --with-zlib --with-pdo-mysql --with-curl --with-ldap --with-curlwrappers --enable-bcmath --with-gettext --with-bz2 --enable-calendar --enable-exif --enable-ftp --with-gd --with-mcrypt --with-mhash --enable-soap --enable-sockets --enable-zend-multibyte --with-tsrm-pthreads --with-jpeg-dir --with-png-dir --with-zlib-dir --with-xpm-dir --with-ttf --with-freetype-dir --enable-gd-native-ttf --enable-safe-mode --with-kerberos --with-sqlite=shared --enable-sqlite-utf8 --enable-gd-jis-conv --enable-zip --with-litespeed

Then follow the instruction on the interface.


