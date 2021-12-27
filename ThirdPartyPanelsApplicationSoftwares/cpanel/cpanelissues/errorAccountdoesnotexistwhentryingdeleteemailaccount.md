---
title: error : Account does not exist ( when trying to delete email account)
description: 
published: true
date: 2021-12-27T15:12:21.768Z
tags: 
editor: markdown
dateCreated: 2021-12-27T15:12:21.768Z
---

# error : Account does not exist ( when trying to delete email account)


```
 error : Account does not exist ( when trying to delete email account)
```

In order to resolve the above error, please do the following steps:

1. Logout of cPanel
1. SSH to the server he is on and do the following commands:

```
$ cd /home/<user>/.cpanel/

$ mv -v email_accounts.yaml email_accounts.yaml.orig

$ mv -v email_accounts.cache email_accounts.cache.orig
```

3. Log back into the cPanel -> Email Account and the issue should have been resolved.
