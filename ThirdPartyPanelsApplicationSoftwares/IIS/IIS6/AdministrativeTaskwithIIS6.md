---
title: Administrative Task with IIS 6
description: 
published: true
date: 2021-09-22T03:23:50.735Z
tags: 
editor: markdown
dateCreated: 2021-09-22T03:23:50.735Z
---


Reference: http://technet.microsoft.com/en-us/library/cc786706(v=ws.10).aspx

## Enabling Web Service Extensions

To enable Web service extensions 

- In IIS Manager, click the Web Service Extensions folder.
- 
- In the details pane, select the Web service extension that you want to enable, and then click Allow.
- 
- To see the properties of a Web service extension, select an extension, and then click Properties.


## Creating Web or FTP Sites

**To use the default Web site** 

1. In IIS Manager, expand the local computer, expand the Web Sites folder, right-click Default Web Site, and then click Properties.

1. On the Web Site tab, under Web site description, type the name of your Web site in the Description box.

1. Click OK. The name of the new site appears in IIS Manager.

**To create a new Web site** 

1. In IIS Manager, expand the local computer, right-click the Web Sites folder, point to New, and then click Web Site. The Web Site Creation Wizard appears.

1. Click Next.

1. In the Description box, type the name of your site, and then click Next.

1. Type or click the IP address (the default is All Unassigned), TCP port, and host header (for example, www.mysite.com) for your site, and then click Next.

1. In the Path box, type or browse to the directory that contains, or will contain, the site content, and then click Next.

1. Select the check boxes for the Web site access permissions you want to assign to your users, and then click Next.

1. Click Finish.

To change these and other settings later, right-click the Web site, and click **Properties**.

**To install FTP services**

1. From the Start menu, click Control Panel.

1. Double-click Add or Remove Programs.

1. Click Add/Remove Windows Components.
 
1. From the Components list box, click Application Server, and then click Details.

1. From the Subcomponents of Application Server list box, click Internet Information Services (IIS), and then click Details.

1. From the Subcomponents of Internet Information Services list box, select the File Transfer Protocol (FTP) Service check box.

1. Click OK twice.

1. Click Next. You might be prompted for the Windows Server 2003 family CD or the network install path.

1. Click Finish, and then click Close.


**To create a new FTP site **

1. In IIS Manager, double-click the local computer, right-click the FTP Sites folder, point to New, and then click FTP Site.

1. Click Next.

1. In the Description box, type the name of your site, and then click Next.

1. Type or click the IP address (the default is All Unassigned) and TCP port for your site, and then click Next.

1. Click the user isolation option you want, and then click Next.

1. In the Path box, type or browse to the directory that contains or will contain shared content, and click Next.

1. Select the check boxes for the FTP site access permissions you want to assign to your users, and then click Next.

1. Click Finish.

## Creating Virtual Directories in IIS 6.0

**To create a virtual directory by using IIS Manager** 

1. In IIS Manager, expand the local computer, expand the Web Sites or FTP Sites folder, right-click the site or folder within which you want to create the virtual directory, point to New, and then click Virtual Directory. The Virtual Directory Creation Wizard appears.

1. Click Next.

1. In the Alias box, type a name for the virtual directory. (Choose a short name that is easy to type because the user types this name.)
 
1. Click Next.
 
1. In the Path box, type or browse to the physical directory in which the virtual directory resides, and then click Next.
 
1. Under Allow the following permissions, select the check boxes for the access permissions you want to assign to your users, and then click Next.
1. Click Finish. The virtual directory is created below the currently selected folder level.

## Renaming Virtual Directories

In IIS 6.0, you cannot use IIS Manager to rename a virtual directory. Instead, you can rename a virtual directory by editing the MetaBase.xml file using a text editor, such as Microsoft Notepad.

**To rename a virtual directory by using Notepad** 

1. Open MetaBase.xml in Notepad. The default location for MetaBase.xml is C:\Windows\System32\Inetsrv.

1. On the Edit menu, click Find, and then locate the virtual directory name that you want to change.

1. Replace the current virtual directory name with a new name.

1. Close the MetaBase.xml file and when prompted, save the changes.

1. In IIS Manager, right-click the local computer, and then select All Tasks.
 
1. On the All Tasks menu, click Save Configuration to Disk

> Note
> When you rename a newly created virtual directory, it takes at least two minutes for the change to appear in IIS Manager if no other changes are pending. To see the change immediately in IIS Manager, close and then reopen IIS Manager.
{.is-info}





