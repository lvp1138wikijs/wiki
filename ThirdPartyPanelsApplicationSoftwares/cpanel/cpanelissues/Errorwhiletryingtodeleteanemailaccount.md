---
title: Error while trying to delete an email account.
description: 
published: true
date: 2021-12-27T15:20:08.190Z
tags: 
editor: markdown
dateCreated: 2021-12-27T15:20:08.190Z
---

# Error while trying to delete an email account.


When you tried to delete an email account from an Addon Domain that was already removed and doesn't exist, the error was: "Account does not exist" . In order to fix this error, please do the following steps:

1) Logout from the cPanel.

2) Log in to your account via SSH as root user and use the following commands.

```
cd /home/<user>/.cpanel/

mv -v email_accounts.yaml email_accounts.yaml.orig

mv -v email_accounts.cache email_accounts.cache.orig
```

3) Log back into the cPanel and select Email Account option and the issue should have been resolved.

