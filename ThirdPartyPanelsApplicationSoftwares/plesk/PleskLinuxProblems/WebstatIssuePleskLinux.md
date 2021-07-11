---
title: Webstat Issue - Plesk Linux
description: 
published: true
date: 2021-07-11T00:38:11.822Z
tags: 
editor: markdown
dateCreated: 2021-07-11T00:38:11.822Z
---

The webstat page https://domain.com/plesk-stat/webstat/ downloading as a PHP file rather than statistics will display in the browser. Its due to PHP parsing is disabled for the /plesk-stat/ directories.

Apache will mark the page as a PHP page and your browser will attempt to download it rather than display it.

- To fix the issue, simply add the LocationMatch to the bottom of your Apache configuration files

```
<LocationMatch "/plesk-stat/(.*)">
AddType text/html .html
</LocationMatch>
```

- Then restart apache service /etc/init.d/httpd restart
- Your web statistics will display in the browser rather than downloading as a PHP file.

