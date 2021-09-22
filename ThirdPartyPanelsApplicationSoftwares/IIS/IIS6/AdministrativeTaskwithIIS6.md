---
title: Administrative Task with IIS 6
description: 
published: true
date: 2021-09-22T04:47:51.986Z
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


## Creating Application Pools in IIS 6.0

**To create a new application pool** 

1. In IIS Manager, double-click the local computer, right-click Application Pools, point to New, and then click Application Pool.

1. In the Application pool ID box, type the name of the new application pool.

1. Under Application pool settings, click either Use default settings for new application pool or Use existing application pool as template.

1. If you selected Use existing application pool as template, from the Application pool name list box, click the application pool to be used as a template.
 
1. Click OK.

## SSL Server Certificate 

**Requesting New SSL Certificate** 

1. In IIS Manager, double-click the local computer, and then double-click the Web Sites folder.

1. Right-click the Web site or file for which you want to request a certificate, and then click Properties.

1. On the Directory Security or File Security tab, under Secure communications, click Server Certificate.
 
1. In the Web Server Certificate Wizard, on the Delayed or Immediate Request page, click Prepare the request now, but send it later. By default, the certificate request file is saved as C:\Certreq.txt, but the wizard allows you to specify a different location.

1. Complete the rest of the steps in the Web Server Certificate Wizard and then click Finish.

1. Send the request to the certification authority. The CA will process the request and then send you the certificate.

**Installing A SSL Certificate**

1. In IIS Manager, expand the local computer, and then expand the Web Sites folder.

1. Right-click the Web site or file that you want, and then click Properties.

1. On the Directory Security or File Security tab, under Secure communications, click Server Certificate.
 
1. In the Web Server Certificate Wizard, click Assign an existing certificate.
 
1. Follow the Web Server Certificate Wizard, which will guide you through the process of installing a server certificate.


## Redirecting Web Sites in IIS 6.0

**To redirect requests to another Web site or directory** 

1. In IIS Manager, expand the local computer, right-click the Web site or directory you want to redirect, and click Properties.

1. Click the Home Directory, Virtual Directory, or Directory tab.

1. Under The content for this source should come from, click A redirection to a URL.
 
1. In the Redirect to box, type the URL of the destination directory or Web site. For example, to redirect all requests for files in the Catalog directory to the NewCatalog directory, type /NewCatalog.

**To redirect all requests to a single file** 

1. In IIS Manager, expand the local computer, right-click the Web site or directory you want to redirect, and click Properties.

1. Click the Home Directory, Virtual Directory, or Directory tab.

1. Under The content for this source should come from, click A redirection to a URL.
 
1. In the Redirect to box, type the URL of the destination file.
 
1. Select the The exact URL entered above check box to prevent the Web server from appending the original file name to the destination URL.

You can use wildcards and redirect variables in the destination URL to precisely control how the original URL is translated into the destination URL.

You can also use the redirect method to redirect all requests for files in a particular directory to a program. Generally, you should pass any parameters from the original URL to the program, which you can do by using redirect variables.

**To redirect requests to a program** 

1. In IIS Manager, expand the local computer, right-click the Web site or directory you want to redirect, and click Properties.

1. Click the Home Directory, Virtual Directory, or Directory tab.

1. Under The content for this source should come from, click A redirection to a URL.

1. In the Redirect to box, type the URL of the program, including any redirect variables needed to pass parameters to the program. For example, to redirect all requests for scripts in a Scripts directory to a logging program that records the requested URL and any parameters passed with the URL, type /Scripts/Logger.exe?URL=$V+PARAMS=$P. $V and $P are redirect variables.

1. Select the The exact URL entered above check box to prevent the Web server from appending the original file name to the destination URL.

## Hosting Multiple Web Sites

1. In IIS Manager, double-click the local computer, right-click the Web Sites folder, right-click the Web site, and click Properties.

1. On the Web Site tab, click Advanced.
 
1. Click Add.

1. In the appropriate boxes, type an IP address, TCP port, and host header value for your Web site.

## Backing Up and Restoring the Metabase in IIS 6.0

IIS administrators can create backup files using IIS Manager or a programmatic administration script. The backup files are copies of the metabase configuration file (MetaBase.xml) and the matching metabase schema file (MBSchema.xml). Using the metabase configuration backup and restore feature, the metabase can be restored from the backup files.

**To create a portable backup (password required)**

1. In IIS Manager, right-click the local computer, point to All Tasks, and click Backup/Restore Configuration.

1. Click Create Backup.

1. In the Configuration backup name box, type a name for the backup file.

1. Select the Encrypt backup using password check box, type a password into the Password box, and then type the same password in the Confirm password box.

1. Click OK, and then click Close.

**To create a non-portable backup (password not required) **

1. In IIS Manager, right-click the local computer, point to All Tasks, and click Backup/Restore Configuration.

1. Click Create Backup.

1. In the Configuration backup name box, type a name for the backup file.

1. Click OK, and click Close.

**To restore the metabase backup **

1. In IIS Manager, right-click the local computer, point to All Tasks, and click Backup/Restore Configuration.

1. In the Backups list box, click the version of the Automatic Backup file that you want to restore, and click Restore. If prompted for a password, type the password you chose to secure the backup.

1. When a confirmation message appears, click Yes.

1. Click OK, and then click Close.

## Enabling ASP.NET

**To enable ASP.NET by using IIS Manager** 

1. In IIS Manager, expand the local computer, and then click Web Service Extensions.

1. In the details pane, click ASP.NET, and then click Allow.

## Enabling ASP Pages in IIS 6.0

1. In IIS Manager, expand the local computer, and then click Web Service Extensions.

1. In the details pane, click Active Server Pages, and then click Allow.

## Starting and Stopping Services

**To restart IIS services **

1. In IIS Manager, right-click the local computer, point to All Tasks, then click Restart IIS.
1. 
1. In the What do you want IIS to do drop-down list, click Restart Internet Services on computer name. You can also choose to reboot the computer, stop the Internet service, or start the Internet service.
1. 
1. IIS attempts to stop all services before restarting.

**To start, stop, or pause individual sites** 

- In IIS Manager, right-click the site you want to start, stop, or pause; and click Start, Stop, or Pause.

## Enabling HTTP Compression

**To enable global HTTP compression by using IIS Manager** 

1. In IIS Manager, double-click the local computer, right-click the Web Sites folder, and then click Properties.

1. Click theService tab, and in the HTTP compression section, select the Compress application files check box to enable compression for dynamic files.

1. Select the Compress static files check box to enable compression for static files.

1. In the Temporary directory box, type the path to a local directory or click Browse to locate a directory. Once a static file is compressed, it is cached in this temporary directory until it expires, or the content changes. The directory must be on the local drive of an NTFS–formatted partition. The directory cannot be compressed or shared, and the access control lists (ACLs) for the directory must include Full Control access to the identity of the application pool or to the IIS_WPG group.

1. Under Maximum temporary directory size, click a folder size option. If you specify a maximum size under Limited to (in megabytes) (the default setting is 95 MB), then when the limit is reached, IIS automatically cleans up the temporary directory by applying the "least recently used" rule.

1. Click Apply, and then click OK.



