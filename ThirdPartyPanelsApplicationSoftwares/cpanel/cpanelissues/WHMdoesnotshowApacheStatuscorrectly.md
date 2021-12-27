---
title: WHM does not show Apache Status correctly
description: 
published: true
date: 2021-12-27T16:16:46.135Z
tags: 
editor: markdown
dateCreated: 2021-12-27T16:16:46.135Z
---

# WHM doe note show Apache Status correctly

If the WHM is not showing the Apache status, make sure that the whm-server-status is added in the configuration. Please follow the steps given below to do that

1) Open the apache configuration file.

```
$ vi /usr/local/apache/conf/httpd.conf
```

2) Then add the following entries in the Apache configuration file and then save.


```
<Location /whm-server-status>

SetHandler server-status

Order deny,allow

Deny from all

Allow from 127.0.0.1

</Location>

ExtendedStatus On
```

3) Now restart apache and it should be showing the apache status correctly in the WHM.


```
$ /scripts/restartsrv_httpd
```



