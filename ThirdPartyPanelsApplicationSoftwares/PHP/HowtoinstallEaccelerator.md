---
title: How to install Eaccelerator
description: 
published: true
date: 2021-12-21T16:56:04.725Z
tags: 
editor: markdown
dateCreated: 2021-12-21T16:56:04.725Z
---

# How to install Eaccelerator

Eaccelerator is a PHP accelerator/encoder/caching utility that is based off of the old mmcache (which is no longer being maintained).

Eaccelerator caches your PHP scripts so that the database is no longer being queried everytime someone needs a script. This is particularly useful for large forums, but pretty much anyone can benefit from it. Since these scripts are cached, you'll notice a decrease in memory use and server load.

1) Login to your server as root user using SSH.

2) Then create eaccelerator directory in the default directory.

```
mkdir /ea/

cd /ea/
```

3) Download the latest eaccelerator file and untar it.

```
wget http://sourceforge.net/projects/eaccelerator/files/eaccelerator/eAccelerator%200.9.6.1/eaccelerator-0.9.6.1.tar.bz2/download
```

Notice that it's a tar.bz2 file, so we need to decompress it twice.

```
bzip2 -d eaccelerator-0.9.6.1.tar.bz2

tar xvzf eaccelerator-0.9.6.1.tar
```

4) install Eaccelerator:

Note: in the following "export" command, you need to point that to where PHP is installed. For most, it's usually either "usr/" or "usr/local", but it may be something else.

```
cd eaccelerator-0.9.6.1

export PHP_PREFIX="/usr"

$PHP_PREFIX/bin/phpize

./configure --enable-eaccelerator=shared --with-php-config=$PHP_PREFIX/bin/php-config

make

make install
```

5) Edit the php.ini file using vi editor.

Find Windows Extensions and  remove the mmcache lines (if you had it installed before) above this.

**For a PHP extension install**:

```
extension="eaccelerator.so"
eaccelerator.shm_size="16"
eaccelerator.cache_dir="/tmp/eaccelerator"
eaccelerator.enable="1"
eaccelerator.optimizer="1"
eaccelerator.check_mtime="1"
eaccelerator.debug="0"
eaccelerator.filter=""
eaccelerator.shm_max="0"
eaccelerator.shm_ttl="0"
eaccelerator.shm_prune_period="0"
eaccelerator.shm_only="0"
eaccelerator.compress="1"
eaccelerator.compress_level="9"
```

**For a Zend extension install**

```
zend_extension="/usr/lib/php4/eaccelerator.so"
eaccelerator.shm_size="16"
eaccelerator.cache_dir="/tmp/eaccelerator"
eaccelerator.enable="1"
eaccelerator.optimizer="1"
eaccelerator.check_mtime="1"
eaccelerator.debug="0"
eaccelerator.filter=""
eaccelerator.shm_max="0"
eaccelerator.shm_ttl="0"
eaccelerator.shm_prune_period="0"
eaccelerator.shm_only="0"
eaccelerator.compress="1"
eaccelerator.compress_level="9"
```

6) Now we need to make the cache directory, where the cache files will be stored.

```
cd ~

mkdir /tmp/eaccelerator/

chmod 0777 /tmp/eaccelerator/

```
7) Restart apache using the coommand

```
service httpd restart
```

Open up your favorite FTP client and upload the eaccelerator.php and eaccelerator_password.php files to any directory on your website.

Once that's done,  go to http://www.your-domain.com/path_to_s...ccelerator.php (of course, replacing that with the path to the script) to see if it's installed.

