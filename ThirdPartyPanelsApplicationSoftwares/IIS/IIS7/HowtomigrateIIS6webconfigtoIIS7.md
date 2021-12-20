---
title: How to migrate IIS6 web.config to IIS7
description: 
published: true
date: 2021-12-20T18:15:53.966Z
tags: 
editor: markdown
dateCreated: 2021-12-20T18:15:53.966Z
---

To migrate IIS6 to IIS7, please follow the procedure below.

Login to your server using an application such as "Remote Desktop Connection."

 

If you are using custom httpHandlers or httpModules, you would need to
run the migration command below.


C:\> %systemroot%\system32\inetsrv\APPCMD.EXE migrate config "domain_name.com/virtual_directory"
Successfully migrated section "system.web/httpModules".
Successfully migrated section "system.web/httpHandlers".

Now if you are going to migate the web.config inside the WEB_ROOT directory itself and not inside any virtual directory don’t miss a forward slash, / after the domain name.

eg:


C:\> %systemroot%\system32\inetsrv\APPCMD.EXE migrate config "domain_name.com/"
Successfully migrated section "system.web/httpModules".
Successfully migrated section "system.web/httpHandlers".

Otherwise you may get an error like below,

ERROR ( message:Cannot find APP object with identifier “domainame.com”. )

Refr : http://blogs.msdn.com/tmarq/archive/2007/08/30/iis-7-0-asp-net-pipelines-modules-handlers-and-preconditions.aspx