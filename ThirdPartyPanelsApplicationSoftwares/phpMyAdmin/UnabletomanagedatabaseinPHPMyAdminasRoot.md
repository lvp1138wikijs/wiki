---
title: Unable to manage database in PHPMyAdmin as Root
description: 
published: true
date: 2021-12-21T18:06:13.636Z
tags: 
editor: markdown
dateCreated: 2021-12-21T18:06:13.636Z
---

# Unable to manage database in PHPMyAdmin as Root

**Question 1**:

```
I have a created a database and a "root"' user for this database with full privilege in Parallels Plesk Panel. However, when I try to open phpMyAdmin as ROOT user, phpMyAdmin shows a "denied access" error.
```

**Question 2**:

```
Unable to manage a database in phpMyAdmin as ROOT, as phpMyAdmin shows a "denied access" error. However, there is no issue with database user.
```

**Reason** :

```
The new version of phpMyAdmin prohibits use of the "root" username by default. Hence it is not possible to manage a database in PHPMyAdmin as a ROOT user.
```

**If you need to allow ROOT user, then manually change phpMyAdmin settings**.


```
Open the @@PRODUCT_ROOT_D@@/admin/htdocs/domains/databases/phpMyAdmin/libraries/config.default.php file
Set the property as follows:
$cfg['Servers'][$i]['AllowRoot'] = true
```

