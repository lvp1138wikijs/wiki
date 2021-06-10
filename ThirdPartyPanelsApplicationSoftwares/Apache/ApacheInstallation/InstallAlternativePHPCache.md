---
title: Install Alternative PHP Cache (APC)
description: 
published: true
date: 2021-06-10T18:22:14.134Z
tags: 
editor: markdown
dateCreated: 2021-06-10T17:30:13.304Z
---

# APC installation

```
wget http://pecl.php.net/get/APC-3.0.19.tgz
tar -xvzf APC-3.0.19.tgz
cd APC-3.0.19
phpize
./configure
make
make install
  
 
pico /usr/local/lib/php.ini
Add extension in php.ini
  
================
  
pecl install apc
  
 
extension_dir ="/usr/local/lib/php/extensions/no-debug-non-zts-20060613/"
extension=apc.so
  
=================
apc.shm_size = 32
apc.shm_segments=1
apc.optimization=0
apc.shm_size=128
apc.ttl=7200
apc.user_ttl=7200
apc.num_files_hint=1024
apc.mmap_file_mask=/tmp/apc.XXXXXX
apc.enable_cli=0
apc.file_update_protection=30
=================

```
