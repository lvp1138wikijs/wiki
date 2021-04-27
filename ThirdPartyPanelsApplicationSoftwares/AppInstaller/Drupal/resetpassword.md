---
title: How to reset the administrator password in Drupal 7
description: 
published: true
date: 2021-04-27T14:42:18.870Z
tags: 
editor: markdown
dateCreated: 2021-04-27T14:42:18.870Z
---


If you want to reset the administrator password, you have to generate a password hash that is valid for your site.

Execute the following commands from the command line, in the Drupal root directory:

```
./scripts/password-hash.sh newpwd

```

Please replace newpwd with your actual new password.

The script will output a password hash that is valid for the site. Copy this to the clipboard or write it down somewhere; you'll need it for the next step. Be careful not to include more or less characters as the hash. These hashes look somewhat like 

```
$S$CTo9G7Lx28rzCfpn4WB2hUlknDKv6QTqHaf82WLbhPT2K5TzKzML
```

Then please login to the database through the command line or through a GUI interface such as phpMyAdmin and execute the following query on the Drupal database:

```
UPDATE users SET pass ='$S$CTo9G7Lx28rzCfpn4WB2hUlknDKv6QTqHaf82WLbhPT2K5TzKzML' WHERE uid = 1;
```

Now you should be able to login to the Drupal using new password.


