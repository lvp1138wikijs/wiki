---
title: Run Cgi Programs Outside Cgi-bin
description: 
published: true
date: 2021-12-27T16:52:49.424Z
tags: 
editor: markdown
dateCreated: 2021-12-27T16:52:49.424Z
---

# Run Cgi Programs Outside Cgi-bin

Add the following lines to the .htaccess file so that perl and cgi programs run can also run in folders other than the cgi-bin folder.

```
AddHandler cgi-script .pl .cgi
Options Includes ExecCGI
```

