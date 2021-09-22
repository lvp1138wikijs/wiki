---
title: Performance Tuning - IIS 6
description: 
published: true
date: 2021-09-22T05:30:59.485Z
tags: 
editor: markdown
dateCreated: 2021-09-22T05:30:59.485Z
---

# Performance Tuning - IIS 6

Reference: http://technet.microsoft.com/en-us/library/cc787182(v=ws.10).aspx

## Enabling HTTP Keep-Alives

1. In IIS Manager, expand the local computer, expand the Web Sites folder, right-click the Web site, and click Properties.

1. On the Web Site tab, in the Connections section, click the Enable HTTP Keep-Alives check box.

1. Click Apply, and then click OK.

## Limiting Connections

**To set a global WWW or FTP service connection limit**

1. In IIS Manager, expand the local computer, right-click the Web Sites or FTP Sites folder, and then click Properties.
 
1. Click the FTP Site tab to limit connections on the FTP service, or click the Performance tab to limit connections on the WWW service.

1. Click the Connections limited to option, and in the box next to it, type the maximum number of simultaneous connections you want to allow on your Web or FTP service.

1. Click Apply, and then click OK.

**To set a Web or FTP site connection limit** 

1. In IIS Manager, expand the local computer, expand the Web Sites or FTP Sites folder, right-click the Web or FTP site on which you want to set the connections limit, and click Properties.
 
1. Click the FTP Site tab to limit connections on the FTP site, or click the Performance tab to limit connections on the Web site.

1. Click the Connections limited to option, and in the box next to it, type the maximum number of simultaneous connections you want to allow on your Web or FTP site.

1. Click Apply, and then click OK.

## Setting Connection Timeouts

**To set a global WWW or FTP service connection time-out value** 

1. In IIS Manager, expand the local computer, right-click the Web Sites or FTP Sites folder, and click Properties.

1. On the Web Site or FTP Site tab, in the Connection timeout box, type the maximum number of seconds that IIS should maintain an idle connection before resetting the connection.

1. For the WWW service, verify that the Enable HTTP Keep-Alives box is selected..

1. Click Apply, and then click OK.

**To set a connection time-out value for a specific Web or FTP site**

1. In IIS Manager, expand the local computer, expand the Web Sites or FTP Sites folder, right-click a Web or FTP site, and click Properties.

1. On the Web Site or FTP Site tab, in the Connection timeout box, type the maximum number of seconds that IIS should maintain an idle connection before resetting the connection.

1. For the WWW service, verify that the Enable HTTP Keep-Alives box is selected.

1. Click Apply, and then click OK.

## Setting the IIS Object Cache Time Period

**To reset the period that unused objects remain in the cache** 

- From the Start menu, click Run, type regedit.exe, and then click OK.

- In the registry editor, navigate to the following subkey:
|    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\InetInfo\Parameters

- Right-click the Parameters subkey, point to New, and then click DWORD Value.
 
- In the New Value box, type ObjectCacheTTL.

- Right-click ObjectCacheTTL, and then click Modify.

- Under Base, click Decimal.

- In the Value Data box, type the number of seconds that you want an unused object to remain in the cache, and then click OK.


The default value is 30 (seconds). You can enter any value from zero, to disable caching, through 4,294,967,295 (unlimited), to disable the object-cache scavenger and allow cached objects to remain in the cache until the cached object changes.


