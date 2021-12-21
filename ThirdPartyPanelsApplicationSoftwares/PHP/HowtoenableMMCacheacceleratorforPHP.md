---
title: How to enable MMCache accelerator for PHP.
description: 
published: true
date: 2021-12-21T16:50:38.390Z
tags: 
editor: markdown
dateCreated: 2021-12-21T16:50:38.390Z
---

# How to enable MMCache accelerator for PHP.


MMCache accelerator is a free open source PHP accelerator, optimizer, encoder and dynamic content cache for PHP. It increases performance of PHP scripts by caching them in compiled state, so that the overhead of compiling is almost completely eliminated. Turck MMCache typically reduces server load and increases the speed of your PHP code by 1-10 times.

MMCache accelerator stores compiled PHP scripts in shared memory and execute code directly from it. It creates locks only for short time while search compiled PHP script in the cache, so one script can be executed simultaneously by several engines.

> Important: If you have ionCube Loader installed this will render it usless and cause all ionCube loader scripts to stop working!
{.is-info}


Turck MMCache does not work in CGI mode.

Please do he following steps to install the MMCache accelerator for PHP.

1) Login as root in SSH.

2) Run the following commands in the following order:

```
cd /

mkdir mmcache

cd mmcache

wget http://sourceforge.net/projects/turck-mmcache/files/turck-mmcache/2.4.6/turck-mmcache-2.4.6.tar.gz/download

tar xzvf turck-mmcache-2.4.6.tar.gz

cd turck-mmcache-2.4.6

export PHP_PREFIX="/usr"
```

Note: This could also be: export PHP_PREFIX="/usr/local"

```
$PHP_PREFIX/bin/phpize

./configure --enable-mmcache=shared --with-php-config=$PHP_PREFIX/bin/php-config

make

make install
```

3) Edit php.ini file using vi editor.

Find this: Windows Extensions

Above this, comment out the PHPA or ZEND lines if you have them. Replace them with this:

To install as a ZEND extension:

```
zend_extension="/mmcache/turck-mmcache-2.4.6/modules/mmcache.so"

mmcache.shm_size="16"

mmcache.cache_dir="/tmp/mmcache"

mmcache.enable="1"

mmcache.optimizer="1"

mmcache.check_mtime="1"

mmcache.debug="0"

mmcache.filter=""

mmcache.shm_max="0"

mmcache.shm_ttl="0"

mmcache.shm_prune_period="0"

mmcache.shm_only="0"

mmcache.compress="1"
```

OR to install as a PHP extension:

```
extension="/mmcache/turck-mmcache-2.4.6/modules/mmcache.so"

mmcache.shm_size="16"

mmcache.cache_dir="/tmp/mmcache"

mmcache.enable="1"

mmcache.optimizer="1"

mmcache.check_mtime="1"

mmcache.debug="0"

mmcache.filter=""

mmcache.shm_max="0"

mmcache.shm_ttl="0"

mmcache.shm_prune_period="0"

mmcache.shm_only="0"

mmcache.compress="1"
```

4) Create the cache directory by doing the following at the command line

```
mkdir /tmp/mmcache

chmod 0777 /tmp/mmcache
```

5) Restart Apache

```
service httpd restart
```

Done!

You can add a phpinfo file on the server to verify whether mmcache is installed correctly. If it installed correctly you will get the following details in the phpinfo.

```
MMCache support enabled

Caching Enabled true

Optimizer Enabled true

Memory Size 33,554,392 Bytes

Memory Available 23,737,176 Bytes

Memory Allocated 9,817,216 Bytes

Cached Scripts 110

Removed Scripts 0

Cached Keys 0
```




