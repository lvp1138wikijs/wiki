---
title: Zencart Admin shows Forbidden Error
description: 
published: true
date: 2021-12-23T15:45:24.824Z
tags: 
editor: markdown
dateCreated: 2021-12-23T15:45:24.824Z
---

# Zencart Admin shows Forbidden Error

**ISSUE**:

```
After installing Zen-Cart from Apps Installer, admin URL gives a 403 error and the site is loading without stylesheet.
```

**ROOT CAUSE**:

```
Maintenance mode is enabled and rewrite rules in .htaccess is causing the issue
```

**SOLUTION**:

```
1) Delete/rename the .htaccess files from admin directory, images directory and from includes directory, after which admin panel will load fine.

public_html/<admin-directory>/.htaccess
public_html/includes/.htaccess
public_html/<admin-directory>/includes/.htaccess
public_html/<admin-directory>/images/.htaccess
2) Then login to admin panel and disable maintenance mode from Admin >> Configuration >> Maintenance mode.
```

Once done zencart will load fine.

