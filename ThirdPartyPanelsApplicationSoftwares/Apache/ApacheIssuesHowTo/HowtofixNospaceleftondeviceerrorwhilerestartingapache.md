---
title: How to fix "No space left on device" error while restarting apache
description: 
published: true
date: 2021-06-16T17:53:14.921Z
tags: 
editor: markdown
dateCreated: 2021-06-16T17:53:14.921Z
---

If you receive the following error while restarting Apache in the server, please try it out the following fix:

```
Error:-
[error] (28)No space left on device: Cannot create SSLMutex Configuration Failed
```

These errors means that there is no available IPC (inter-process communication) resources in the system, such as semaphores or shared memory segments. In order to check IPC resources in the system, please use the 'ipcs' command as follows:

```
$ ipcs -a
...
------ Semaphore Arrays --------
key        semid      owner      perms      nsems
0x00000000 201293824  apache    600        1
...
```

You will be able to see a lot of semaphores under Apache . You need to kill those processes using the following script and restart apache.

```
$ ipcs -s | grep apache | perl -e 'while (<STDIN>) {@a=split(/\s+/); print `ipcrm sem $a[1]`}'
$ service httpd restart
```


