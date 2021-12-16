---
title: Starting With IIS 6
description: 
published: true
date: 2021-12-16T18:10:12.405Z
tags: 
editor: markdown
dateCreated: 2021-12-16T18:10:12.405Z
---


**Procedure Applies To**: Windows Server 2003, Windows Server 2003 R2, Windows Server 2003 with SP1

**More Reference**: http://technet.microsoft.com/en-us/library/cc775921(v=ws.10).aspx

### **Installing IIS**

**To install IIS using the Configure Your Server Wizard**

- From the Start menu, click Manage Your Server.
- 
- Under Managing Your Server Roles, click Add or remove a role.
- 
- Read the preliminary steps in the Configure Your Server Wizard and click Next.
- 
- Under Server Role, click Application server (IIS, ASP.NET) and then click Next.
- 
- By default, the wizard installs and enables IIS, COM+, and DTC.
- 
- If you want to serve either of the optional technologies (FrontPage Server Extensions or ASP.NET), on the Application Server Options page, select the appropriate check boxes, and then click Next.
- 
- Read the summary and click Next.

- Complete the wizard, and then click Finish.



### **IIS Directories**

IIS installs the following directories:

- \InetPub
- systemroot\Help\IISHelp
- systemroot\System32\InetSrv
- systemroot\System32\InetSrv\MetaBack



### IIS Initial Configuration Backup

When you first install IIS, a backup of the initial metabase configuration is automatically created in the systemroot\System32\InetSrv\MetaBack directory. This backup can be used to restore the IIS configuration to its state immediately following IIS installation. This is a useful tool for solving metabase corruption or configuration problems, and can help you recover a known good configuration without needing to reinstall IIS.

This backup is not password protected, and can only be used to restore settings on the system on which it was created. See Backing Up and Restoring the Metabase in IIS 6.0 for information about restoring the initial IIS configuration backup.

It is strongly recommended that following IIS installation, and before any configuration changes are made, you create a password-protected backup of the IIS configuration. Unlike the automatic initial configuration backup, a password-protected backup is system independent, and can be used to restore settings on other systems running IIS 6.0. See Backing Up and Restoring the Metabase in IIS 6.0 for information about creating a password-protected backup of the IIS configuration.



### IIS Manager

IIS Manager is a graphical interface for configuring your application pools or your Web, FTP, SMTP, or NNTP sites. With IIS Manager, you can configure IIS security, performance, and reliability features. You can add or delete sites; start, stop, and pause sites; back up and restore server configurations; and create virtual directories for better content management, to name only a few of the administrative capabilities.

**To start IIS Manager** 

From the Start menu, point to Administrative Tools, and then click Internet Information Services (IIS) Manager.


1. From the Start menu, click Run.
1. In the Open box, type inetmgr, and click OK

You can also access IIS from the Computer Management window. Accessing IIS in this way does not give you the range of administration options offered by IIS Manager; however, it does offer quick access and limited management options for your Web sites.


### To start IIS Manager from the Computer Management window 

1. From the Start menu, right-click My Computer, and click Manage.

1. In the console tree, expand the Services and Applications node.

1. Click Internet Information Services. The names and states of your Web sites appear in the details pane.
 
1. In the console tree, expand the Internet Information Services node and any subsequent Web site nodes to see a list of directories and virtual directories for that Web site.

### Uninstalling IIS

To uninstall IIS using the Configure Your Server Wizard 

1. From the Start menu, click Manage Your Server.

1. Under Managing Your Server Roles, click Add or remove a role.

1. Read the preliminary steps in the Configure Your Server Wizard and click Next.

1. Under Server Role, click Application server (IIS, ASP.NET) and then click Next.

1. In the Role Removal Configuration dialog, check the Remove the application server role check box.

1. Complete the wizard, and then click Finish.


