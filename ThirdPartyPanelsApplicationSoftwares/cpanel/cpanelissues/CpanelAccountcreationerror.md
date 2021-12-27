---
title: Cpanel Account creation error
description: 
published: true
date: 2021-12-27T14:36:36.656Z
tags: 
editor: markdown
dateCreated: 2021-12-27T14:36:36.656Z
---

# Cpanel Account creation error


While creating an account via WHM, you may get an error stating that, cannot create new user and the account creations fails.

You can check the cPanel logs for the error.

```
#tail -f /usr/local/cpanel/logs/error_log
```

Sometimes, you may get the following error.

```
vipw lockfile (/etc/ptmp) is present!
```

This means that the "useradd" is locked. You will not be able to add new users unless you remove the following file.

You can also confirm it by executing the useradd command in the konsole. You will receive an error message stating the above.

```
#useradd testing
```

To resolve the issue, Check if this file is present.

```
ll /etc/ptmp
```

/etc/ptmp  >> This has a temporary copy of the password file. This file can be removed.


```
rm -f /etc/ptmp
```

Now try to add the domain and it should be working fine. 

