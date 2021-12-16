---
title: Website Setup - IIS 6
description: 
published: true
date: 2021-12-16T18:56:37.363Z
tags: 
editor: markdown
dateCreated: 2021-12-16T18:56:37.363Z
---

> Reference: http://technet.microsoft.com/en-us/library/cc785214(v=ws.10).aspx
{.is-info}


**Creating a Web Site from a Template**

**To create a Web site template file** 

1. In IIS Manager, double-click the local computer, right-click the site or application that you want to back up, point to All Tasks, and then click Save Configuration to a File.

1. In the Save Configuration to a File dialog box, in the File name box, type a file name.

1. In the Path box, type the full path to the configuration file, or click Browse to browse to the location where you want to save the file, and then click OK.

**To create a new site from a template file **

1. In IIS Manager, double-click the local computer, right-click the Web Sites folder, point to New, and then click Web Site (from file).

1. In the Import Configuration dialog box, in the File box, type the full path to the configuration file, or click Browse to browse for the file.

1. Click Read File.

1. The Select a configuration to import box is populated.

1. In Select a configuration to import, click the configuration that you want to import, and then click OK.

### Setting Home Directories

**To change the home directory of a Web site using IIS Manager** 

1. In IIS Manager, expand the local computer, expand the Web Sites directory, right-click the Web site you wish to change, and click Stop.

1. Use Windows Explorer, to rename the LocalDrive:\Inetpub\Wwwroot directory to the name of your choice. Alternatively, you can copy the entire \Wwwroot directory tree to a new location.

1. In IIS Manager, right-click your Web site, and click Properties.
 
1. Click the Home Directory tab, and under The content for this resource should come from, click A directory located on this computer, A share located on another computer, or A redirection to a URL, depending on where your home directory is located.

1. In the Local path box, type the path name, share name, or URL of your directory.

1. In IIS Manager, expand the Web Sites folder, right-click the Web site you just changed, and click Start.


### Setting Up Default Documents

**To set up or change the default document** 

1. In IIS Manager, double-click the local computer, right-click the Web Sites folder or an individual Web site folder, and then click Properties.

1. Click the Documents tab.

1. Select the Enable default content page check box.
 
1. Click Add to add a new default document to the list.

1. Click the document you want to remove from the list and click Remove.

1. Click a document from the list and click Move Up or Move down to change the order in which default documents are served to client requests.
 
1. Click OK.

### Using Virtual Directories

**To create a virtual directory using the Virtual Directory Creation Wizard **

1. In IIS Manager, double-click the local computer, double-click the Web site or FTP site to which you want to add a virtual directory, right-click the Web Site or folder within which you want to create the virtual directory, point to New, and then click Virtual Directory.

1. Click Next.

1. In the Alias box, type a name for the virtual directory, and then click Next. The alias is the name that the user types, and it should be short and easy to type.

1. In the Directory box, type or browse to the physical directory in which the virtual directory resides, and then click Next.
 
1. In the Access Permissions dialog box, set the access permissions appropriate to your needs.

1. Click Next, and then click Finish.


### Creating Multiple Sites Using Host Header Names

**To add a Web site using a host header identifier using the Web Site Creation Wizard** 

1. In IIS Manager, expand the local computer, right-click the Web Sites directory, point to New, and then click Web Site.

1. Click Next.

1. In the Description box, type the name you have selected for the Web site, and then click Next.

1. In the Enter the IP address to use for this Web site box, click the IP address used by all sites on the server.

1. In the TCP port this Web site should use box, type the port number used by all sites on the server.

1. In the Host Header for this Web site (Default:None) box, type the host header name to identify the Web site. The host header name must contain the full name of the site, for example, www.serverpoint.com.

1. If SSL encryption is not enabled on the server, the SSL port box does not appear. If SSL encryption is enabled on the server, type the SSL port number, and then click Next. Note that you cannot use host headers with SSL encryption.
 
1. In the Path box, type or browse to the path of your Web site home directory.

1. To create a secured or private Web site, clear the Allow anonymous access to this Web site check box, and click Next. (Web sites are configured for anonymous access by default.)
 
1. In the Web Site Access Permissions box, set the permissions for the home directory.

1. Click Next, and then click Finish.


### Creating Multiple Sites Using Multiple IP Addresses

**To add a Web site using a unique IP address identifier using the Web Site Creation Wizard** 

1. In IIS Manager, expand the local computer, right-click the Web Sites directory, point to New, and then click Web Site.

1. Click Next.

1. In the Description box, type the name you have selected for the Web site, and click Next.

1. In the Enter the IP address to use for this Web site box, click the unique IP address reserved for this site.

1. In the TCP port this Web site should use box, type the port number used by all sites on the server. This should typically be left at the default of 80.

1. If SSL encryption is enabled on the server, type the SSL port number, and then click Next. If SSL encryption is not enabled on the server, the SSL port box does not appear.

1. In the Path box, type or browse to the path of your Web site home directory.

1. To create a secured or private Web site, clear the Allow anonymous access to this Web site check box, and then click Next. (Web sites are configured for anonymous access by default.)

1. In the Web Site Access Permissions box, set the permissions for the home directory.

1. Click Next, and then click Finish.





