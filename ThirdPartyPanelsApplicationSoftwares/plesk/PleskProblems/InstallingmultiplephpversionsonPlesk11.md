---
title: Installing multiple php versions on Plesk 11.5.x
description: 
published: true
date: 2021-07-18T05:04:57.016Z
tags: 
editor: markdown
dateCreated: 2021-07-18T05:04:57.016Z
---

# Installing multiple php versions on Plesk 11.5.x


I will going to install php 5.2.17

Install required packages to compile php

```
apt-get install libxml2-dev make gcc g++ libxml2-dev libpcre3-dev libbz2-dev libcurl4-openssl-dev libdb4.8-dev libjpeg-dev libpng12-dev libxpm-dev libfreetype6-dev libmysqlclient-dev libt1-dev libgd2-xpm-dev libgmp-dev libsasl2-dev libmhash-dev unixodbc-dev freetds-dev libpspell-dev libsnmp-dev libtidy-dev libxslt1-dev libmcrypt-dev libc-client-dev -y
```
Installing php 5.2.17

```
mkdir /root/php52
cd /root/php52
wget http://museum.php.net/php5/php-5.2.17.tar.gz
tar xzvf php-5.2.17.tar.gz
cd php-5.2.17
```

Dependency # 01

```
wget https://bugs.php.net/patch-display.php?bug_id=54736&patch=debian_patches_disable_SSLv2_for_openssl_1_0_0.patch&revision=1305414559&download=1
mv debian_patches_disable_SSLv2_for_openssl_1_0_0.patch.patch.txt debian_patches_disable_SSLv2_for_openssl_1_0_0.patch.patch
patch -p1 < debian_patches_disable_SSLv2_for_openssl_1_0_0.patch.patch
```

You should see friendly success messages like these:

```
patching file ext/openssl/xp_ssl.c
Hunk #1 succeeded at 332 (offset 4 lines).
Hunk #2 succeeded at 354 (offset 4 lines).
Hunk #3 succeeded at 583 (offset -50 lines).
Hunk #4 succeeded at 819 (offset -98 lines).
```

Dependency # 02

```
ln -s /usr/lib/libc-client.a /usr/lib/x86_64-linux-gnu/libc-client.a
```

Dependency # 03

```
nano -c ext/gmp/gmp.c
 
Go to line # 1399
 
Replace
__GMP_BITS_PER_MP_LIMB with GMP_LIMB_BITS
```

```
./configure --with-libdir=lib/x86_64-linux-gnu --cache-file=./config.cache --prefix=/usr/local/php52 --with-config-file-path=/usr/local/php52/etc --disable-debug --with-pic --disable-rpath --with-bz2 --with-curl --with-freetype-dir=/usr/local/php52 --with-png-dir=/usr/local/php52 --enable-gd-native-ttf --without-gdbm --with-gettext --with-gmp --with-iconv --with-jpeg-dir=/usr/local/php52 --with-openssl --with-pspell --with-pcre-regex --with-zlib --enable-exif --enable-ftp --enable-sockets --enable-sysvsem --enable-sysvshm --enable-sysvmsg --enable-wddx --with-kerberos --with-unixODBC=/usr --enable-shmop --enable-calendar --with-libxml-dir=/usr/local/php52 --enable-pcntl --with-imap --with-imap-ssl --enable-mbstring --enable-mbregex --with-gd --enable-bcmath --with-xmlrpc --with-mysql=/usr --with-mysqli --with-snmp --enable-soap --with-xsl --enable-xmlreader --enable-xmlwriter --enable-pdo --with-pdo-mysql --with-pear=/usr/local/php52/pear --with-mcrypt --without-pdo-sqlite --with-config-file-scan-dir=/usr/local/php52/php.d --enable-fastcgi
make
make install
cp php.ini-recommended /usr/local/php52/etc/php.ini
/usr/local/psa/bin/php_handler --add -displayname "5.2.17-custom" -path /usr/local/php52/bin/php-cgi -phpini /usr/local/php52/etc/php.ini -type cgi -id "5.2.17-custom"
/etc/init.d/apache2 restart
```

Now you can login to plesk >> Subscriptions

Click on Manage hosting for domain you want to change php version, then click on "hosting setting"

Select in "PHP support"

```
Run PHP as "CGI application" PHP version "5.2.17-custom"
```

and your domain will start using php 5.2.17

 

 

Ref: http://download1.parallels.com/Plesk/Doc/en-US/online/plesk-administrator-guide/index.htm?fileName=72042.htm

http://zgadzaj.com/how-to-install-php-53-and-52-together-on-ubuntu-1204

