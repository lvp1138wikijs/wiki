---
title: Fatal error: Cannot run code from this file in conjunction with non encoded files
description: 
published: true
date: 2021-06-16T16:50:13.624Z
tags: 
editor: markdown
dateCreated: 2021-06-16T16:50:13.624Z
---

If you are getting the error " Fatal error: Cannot run code from this file in conjunction with non encoded files in filename.php"  in APC enabled servers, use the fix given below:

- Add the apc filter for this file in php.ini file. 

1. In php.ini under extension=apc.so add

```
apc.filters="filename.php"
```

2. Save and restart Apache

```
# service httpd restart
```


