---
title: phpmyadmin:unable to access
description: 
published: true
date: 2021-12-27T15:56:18.105Z
tags: 
editor: markdown
dateCreated: 2021-12-27T15:56:18.105Z
---

# phpmyadmin:unable to access

If you get the following error while trying to access phpmyadmin from your cpanel account:

```
This feature is not available while logged in with root override. You are logged in with the root, or reseller's password. Please login with this user's account password or go back.
```

**Solution**:

- Make sure your cpanel account is having a different password from  your root or reseller password.
- Follow the steps below to change your cpanel account's password.

```
WHM >> Account Functions >> Password Modification

select account, enter new password and click "Change password" button.
```

