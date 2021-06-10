---
title: How to install mod_xsend module
description: 
published: true
date: 2021-06-10T18:20:53.121Z
tags: 
editor: markdown
dateCreated: 2021-06-10T17:28:58.953Z
---


> mod_xsend file is a small Apache2 module that processes X-SENDFILE headers registered by the original output handler. 
> 
> If it encounters the presence of such header it will discard all output and send the file specified by that header instead using Apache internals including all optimizations like caching-headers and sendfile or mmap if configured.
> 
> It is useful for processing script-output of e.g. php, perl or any cgi.
{.is-info}

In order to install mod_xsend module, please do the following steps:

1.Download mod_xsend, extract it, then change to the newly created directory.

```
$ wget https://www.tn123.org/mod_xsendfile/mod_xsendfile-0.12.tar.gz

$ tar -xzvf mod_xsendfile-0.12.tar.gz

$ cd mod_xsendfile-0.12
```

2.Compile and install

```
apxs -cia mod_xsendfile.c
```

3.Restart Apache .

```
/etc/init.d/httpd restart
```

4. For viewing mod_xsend module install or not, you can use either the command httpd -M or calling phpinfo .


**Advantage**:

The advantages of xsendfile come from dealing with bigger files. If you try reading a big file into memory for sending through PHP, or otherwise send one through PHP, you may hit various roadblocks:

- You may hit the PHP memory limit
- You may hit PHP’s max execution time limit

If you don’t encounter these two, you may find that sending the file through the PHP process is slower, or it may eat more memory from your server than if it was sent by Apache.

mod_xsendfile solves all these problems.