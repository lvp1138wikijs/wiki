---
title: Apache Error – No space left on device: Couldn’t create accept lock
description: 
published: true
date: 2021-06-16T16:41:26.254Z
tags: 
editor: markdown
dateCreated: 2021-06-16T16:41:26.254Z
---

Sometimes Apache (HTTPD) service on a Server stops and while restart it shows following messages in error_logs.

```
[Wed Jul 31 04:43:31 2013] [crit] (28)No space left on device:

mod_rewrite: Parent could not create RewriteLock file

/usr/local/apache/logs/rewrite_lock

Configuration Failed
```

Such errors appears when you are running out of Disk Space or Quota which is assigned (which can be increased to fix the issue) OR when semaphores of the server gets full. Semaphores are often used to restrict the number of threads than can access some (physical or logical) resource.

For viewing semaphores list, please execute  following command:

```
# ipcs -s | grep nobody
```

In-order to clear the semaphores list, execute the following command.

```
# ipcs -s | grep nobody | awk '{print $2}' | xargs -n 1 ipcrm sem
```

Then restart the apache server and it will starts without any issues.But, it is a temporary solution and it will re-occur when Semaphores get full.

In order to fix those issues permanently, please do the following changes in  /etc/sysctl.conf . These values will increase the limits of Semaphores on the Server.

```
# Increases the semaphore limits & extend Apache's uptime.
kernel.msgmni = 512
kernel.sem = 250 128000 32 512
```

Then load the new settings into the kernel using the command.

```
# sysctl -p
```

