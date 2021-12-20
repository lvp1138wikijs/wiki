---
title: IIS How Tos
description: 
published: true
date: 2021-12-20T19:02:33.176Z
tags: 
editor: markdown
dateCreated: 2021-12-20T19:02:33.176Z
---

# IIS How Tos


## Add a Virtual Directory to a Site in IIS7

A virtual directory is a directory name (also referred to as path) that you specify in IIS and map to a physical directory on a local or remote server. The directory name then becomes part of the application's URL, and users can request the URL from a browser to access content in the physical directory, such as a Web page or a list of additional directories and files. If you specify a different name for the virtual directory than the physical directory, it is more difficult for users to discover the actual physical file structure on your server because the URL does not map directly to the root of the site.

1. Log into your server using RDP.

2. Click on start and then administrative tools and then Internet Information Services (IIS)Manager

3. Click the plus sign next to your server name to expand it.

4. Click the plus sign next to Sites to expand it.

5. Right click on the site you wish to add a virtual directory too and click Add Virtual Directory.

6. Fill in the alias field and the path to the folder for which you wish to create the virtual directory for.

7. Click OK

## Add FTP User to FTP 7 Windows 2008

**Create Local User**

The first step is to create the user on your server. All FTP users are local users assigned to your server through users and groups management. Please follow the steps below.

1. Open Server Management by navigating to Start Menu --> Control Panel --> Administrative Tools --> Server Manager.

2. Expand Configuration and then expand Local Users and Groups.

3. Right click on users and click on add new user. Fill in the form and choose user cannot change password and password never expires.

**Add User to FTP Site in IIS**

1. Open IIS and expand sites by clicking the +. Find the site labeled "FTP" and click the + next to it to expand the site as well. Right click on the folder named “LocalUser” and click on add virtual directory.

For the Add Virtual Directory window, follow the convention below.

- Alias: The user name for the FTP user.
- Physical path: The folder you want to give the user access to.

2. Click ok after typing in the user name and choosing the folder. This will create a virtual directory under the folder LocalUser under the FTP site.Click once on this folder and then double click on FTP Authorization Rules. 

3. Remove the all users rule by clicking on it and then then click remove on the right hand side.

4. Click on Add Allow Rule and choose the bubble next to specified user. Type in the user name you added and then give it the permissions desired.

**NTFS Permissions**


Now that the user is added to IIS we need to add permissions to the directory it has access to. This is done through NTFS permissions.

1. Click on the virtual directory you created for the user in IIS and on the right hand side click on Edit Permissions

2. Click on the security tab and then click on Edit.

3. Click on the add button and click cancel if you receive a login prompt.

4. Type in the user name as "Servername\username". IE: exam321\user.

Typing the server name first will avoid getting any popups asking for a user name and password. If you do receive this popup simply cancel. Your server is part of our domain and when you add users it tries to query the active directory server which you do not have access to. Alternatively you can click on Locations and then choose your server as the location. After choosing the location type in the user name or click on advanced and find now. Click ok to add the user to permissions

5. Now you simply click on the user and choose the permissions you wish to give that user. If the user needs to be able to upload files and create folders, you will need to give that user Modify permissions. If the user only needs read access, then read and List folder contents is all you need. 

**Permissions**

- Full Control - This is meant for administrators and system users, never use this for a FTP user.
- Modify - Checking this box will automatically give all the correct permissions for read and write access.
- Read & Execute - Read access with ability to execute programs.
- List folder contents - Ability to list out folders.
- Read - Simple read access to files only, remember to check list folder contents as well for read access.
- Write - Ability to upload and create folders.
- Special Permissions - Never used for FTP users, these are custom permissions.

After you choose the permissions and click ok you're done. You can test the FTP user by connecting with a FTP client.


## Add virtual directory as application in IIS 7


A virtual directory is a directory name alias (also referred to as path) that you specify in IIS and map to a physical directory on a local or remote server. The directory name then becomes part of the application's URL, and users can request the URL from a browser to access content in the physical directory, such as a Web page or a list of additional directories and files. If you specify a different name for the virtual directory than the physical directory, it is more difficult for users to discover the actual physical file structure on your server because the URL does not map directly to the root of the site. 

Setting up a virtual directory as an application will allow you to run ASP.NET applications and also allow you to configure the virtual directory separately from the main site. Normally all settings and configuration will be inherited from the parent site or IIS server.

1. Log into your server using RDP.

2. Click on start and then administrative tools and then Internet Information Services (IIS) Manager

3. Click the plus sign next to your server name to expand it.

4. Click the plus sign next to Sites to expand it.

5. Right click on the site you wish to add a the virtual directory as an application too.

6. Click Add Virtual Directory.

6. Fill in the alias field and the path to the folder for which you wish to create the virtual directory for.

7. Click OK

8. Expand the site you just added the virtual directory to and right click on your new virtual directory.

9. Click convert to application and then click OK


## Change asp.net version in IIS 7

1. Login with remote desktop and open Internet Information Services on the windows 2008 server. This is found under Start Menu, Control Panel, Administrative Tools, Internet Information Services (IIS) Manager.

2. Click on the + next to your server name and then click on Application Pools.

3. Locate the application pool for the website you are changing asp.net for. Right click on the application pool and click on Basic Settings.

4. From the drop down menu under .NET Framework Version choose the version of asp.net you wish the site to run on. If asp.net 1.x or any other version you wish to use does not appear it will need to be installed.

## Change content location of a domain in IIS 7

The content location of your domain is the folder in which you tell the server to look for the default documents to display your site. This directory normally contains all of your web content including images, files, etc.

1. Login to your Server through Remote Desktop.

2. Click on Start, Administrative Tools, Internet Information Services (IIS) Manager.

3. Click the plus sign next to your server to expand it.

4. Click the plus sign next to the sites folder to expand it.

5. Click on the site you wish to change the content location for.

6. On the far right pane click on the Basic Settings option.

7. Click on the ... button next to the Physical path text field to navigate to the folder you wish to select. Or you can simply type in the location

8. Click ok

## Change managed pipeline mode in IIS 7 or Fix certain codes issues


If you are running into odd errors on your site or cannot get a piece of code to work properly it may be the managed pipeline mode is incorrect. You can change this under the basic settings of the application pool. Often setting this to classic will resolve issues. Follow the instructions below to change the managed pipeline mode in IIS 7.

In IIS 7.0, there are two request-processing modes for application pools: integrated mode and classic mode. When you configure an application pool with integrated mode, IIS processes requests for managed content with the new integrated IIS and ASP.NET request processing pipeline. When you configure an application pool with classic mode, IIS continues to process requests for managed content using the separate IIS and ASP.NET request-processing pipelines. Use classic mode only for applications that cannot run in integrated mode.

1. Login with remote desktop and open Internet Information Services on the windows 2008 server. This is found under Start Menu, Control Panel, Administrative Tools, and then Internet Information Services (IIS) Manager.

2. Click on the + next to your server name and then click on Application Pools.

3. Locate the application pool for the website you are changing asp.net for. Right click on the application pool and click on Basic Settings.

4. From the drop down menu under Managed pipeline mode: choose classic then click on ok. (Integrated is the default mode.)


## Create an application pool in IIS 7

You can create an individual application pool in IIS 7 for Windows Server 2008 by performing the following steps.

it is recommended that each site and application on your server have its own application pool. By default when you create a new website in IIS 7 a new application pool is created.

1. First open Internet Information Services on the windows 2008 server. This is found under Start Menu , click Control Panel, click Administrative Tools, and then clcik Internet Information Services (IIS) Manager.

2. Navigate to application pools in IIS by expanding the server.

3. Right click on Application Pools and select Add Application Pool.

- **Name**: This can be the domain name the application pool is for or a simple description of the site it will be for or the application.
- .**Net Framework Version**: The version of asp.net you would like to use. 2.x for new applications using asp.net 2.x or 3.x. Version 1.x for classic applications.
- **Managed Pipeline Mode**: Select either integrated or classic. Classic if you are going to run an asp.net 1.x application.

4. After you have created the application pool go back to your site in IIS under “Sites” and changed the application pool it uses to your new one.


## Set Custom error pages on your server

Custom error pages are used to redirect visitors when they access old parts of your site no longer available or run into an error with the site yourself. They look moire professional and can allow your visitors to go back to your home page easily. If you would like to create your own custom error pages on your dedicated server here are the basic steps you will need to take.

1. Log into your dedicated server using RDP.

2. Click on start.

3. Click on administrative tools.

4. Click on Internet Information Services.

5. Click on the name of your server.

6. On the right hand side double click on the icon for error pages.

7. On the far right you can now click on the Add option. 

8. The Add Custom Error Page configuration box will open up

9. Type in the error code for the error you wish for your custom error page to display for.

10. Click on the brows option and navigate to your custom error page.

11. Click ok.

## How to Disable Logging on Websites

Disabling logging on sites that do not require it can help with server performance by lowering disk IO as well as help you maintain disk space. Follow the instructions below to disable logging on a website in IIS 7 and then delete the log files.

1. Open IIS and click on the + next to your server name then the + to expand sites. Click on the site you wish to disable logging for and then double click the icon in the center of the window called logging.

*Note: Logging can be disabled for all sites by clicking on your server name in IIS and then clicking on the logging icon.

2. On the right hand side of the IIS window click on the link that says "disable". The action takes effect immediately.

3. Click on Sites on the left hand side of the IIS window. In the middle note the ID number of the site you just disabled. The ID number is under the column ID. You will need to know this to delete the logs.

3. To delete the log files that were already created open computer from the start menu and navigate to

C:\inetpub\logs\logfiles

You will probably find several folders for each site on your server. Each folder is named W3SVC#, for example W3SVC1 for the first site created in IIS. You can figure out what site you just disabled by looking for it's ID number after W3SVC. So if your site had an ID number of 33 you would look for the folder titled W3SVC33. Now all you need to do is delete it.

## Enable logging in IIS 7

Logging is used for statistics on your web server. Logs need to be enabled for stats software to function properly as they import the log file and then analyze them. Stats software is used for SEO purposes. Logging can also be used to track issues with your website as well.

1. Login to your Server through Remote Desktop.

2. Open Internet Information Services MMC snap in from administrative tools.

3. Click on the machine name and then click on Logging in the IIS portion.

4. Click on Enable on the right hand side of the window.

5. Click on Select Fields to select what information you would like logged. After you are done click on apply.

6. Log files and folders will be created in C:\Inetpub\logs\LogFiles once a site is visited.

7. Each folder will contain the logs for each site. You can determine what site corresponds to what directory by viewing the site's ID number in IIS. To do this click on sites in IIS and locate the ID number under the column ID next to the site name. The directory for that site will be W3SVCx with "x" being the ID number from IIS.


## Enable parent paths on your server in IIS7


In earlier versions of IIS, parent paths was enabled by default. In IIS 6.0 the default behavior changed to disabled parent paths, and this was done for security and design reasons. If you need to enable parent paths please follow the steps below:

1. log into your server via RDP.

2. click on Start > Administrative Tools > Internet Information Services Manager (iis).

3. On the left of the screen click the + sign next to your server name.

4. Click the + sign next to sites.

5. Click on the site you wish to enable parent paths for.

6. On the right side of the screen you will see the site options. Double Click on the ASP option

7. Then click next to the option Enable Parent Paths and select the true option from the drop down.

8. Select the Apply option on the top right of the screen and your all set.

## Setting Default Documents on a Site

Login to your Server through Remote Desktop.

1. Open up Internet Information Services (IIS) Manager from your Administrative Tools Menu. Click on the Start Menu --> Control Panel --> Administrative tools.

2. Once inside of the IIS Manager, click on the + sign next to the server name to expand sites and applications pools.

3. Click on the + sign next to "Sites" in IIS Manager in order to see a list of websites on the server.

4. Click on the website you wish to set the Default document on in order to bring up a list of site settings in the main window.

5. In the main window, click on the Default Document Icon under the IIS section.

6. A list of default documents will come up. Use the options in the upper right corner to add, remove, or change the order of the default documents listed.

A default document can be named anything, but commonly it is either index or default. Make sure to include the file extension as well, for example .asp for classic asp, and .php for PHP.

## Stop an application pool in IIS on your Server

An application pool is a group of one or more URLs that are served by a worker process or a set of worker processes. Application pools set boundaries for the applications they contain, which means that any applications that are running outside a given application pool cannot affect the applications in the application pool. Sometimes your application pool will become overloaded or error due to a number of different reasons. You may want to start and stop this pool on some occasions and you can do so by following the directions below.

1. Login to your Server through Remote Desktop.

2. Click start, Administrative Tools, and then Internet Information Services (IIS) Manager.

3. Click on the plus sign in the left next to your server to expand it.

4. Click on Application Pools.

5. In the right pane find the application pool you wish to stop and right click on it.

6. Click stop.

## What are the Common PHP settings in IIS 7

Using FastCGI, PHP support is available in IIS 7. In general, settings for your PHP applications can be controlled within your code. The only exception to this is the php.ini file. This file is no longer unique to each website. Instead, a single php.ini file is used globally by the server and automatically inherited by all PHP applications.

As a result, there are specific settings that are set on the server that cannot be changed. These settings have been selected based on the application requirements, server stability and server security. Below is a list of specific settings and what they are set to:


- safe_mode = off
- registered_globals = off
- display_errors = off
- memory_limit = not more than 12MB
- post_max_size and upload_max_filesize = not more than 15 mb


## How to Configure virtual hosts in IIS FTP

1) Log into the server through a Remote Desktop Connection

2) On the Start menu, click Administrative Tools, and then click Internet Information Services (IIS) Manager. In the Connections pane, expand the Sites node in the tree by clicking on it.

3) Right click on the site you wish to install the FTP service for and select Add FTP publishing

4) Choose an IP address for your FTP site from the IP Address drop-down, or choose to accept the default selection of "All Unassigned."

5) Enter the TCP/IP port for the FTP site in the Port box.

6) Enter "www.example.com" in the Virtual Host box.

7) Select No SSL radio button unless you have a certificate you wish to connect securely with

8) Click Next

9) In Authentication settings, select Basic

10) Choose "Specified users" from the Allow access to drop-down

11) Type <your_username> for the user name in the field below

12) This will grant only this user access to the specified directory, you can also allow anonymous or all users access to this directory as well.

13) In the Permissions option, select read and write.

14) Click Finish


## Install IIS SMTP for a Windows 2008 server

This article will explain how to install IIS SMTP for Windows 2008.


1. Log into your server through Remote Desktop Connection 
1. Open Server Manager under Start > All Programs > Administrative Tools
1. Click Features > Add Features
1. Check the checkbox for SMTP Server
1. A warning may pop up asking to install related software as part of the SMTP installation process. ClickAdd Require Features. Then click Next
1. Then click Install and the SMTP services within IIS 6 will be installed once completed.

Once installed, navigate to Start > All Programs > Administrative Tools and open Internet Information Services (IIS) Manager 6. Drill down and you will see Default SMTP Server which is where the software can be configured.


## Preview your site on a Windows Server with IIS 7 Host Headers

Let's make an example per say that your server IP address is 1.2.3.4 and your domain is mydomain.com. You are working on the site and want to test the site on your server at Hosting.com however you are not ready to update DNS just yet.

For this tutorial it is important to under host headers and how to set them inside of IIS

1. Start > Run > inetmgr <enter>
1. Expand Sites
1. Right Click on Web Site to be Adjusted and Choose Edit Bindings
1. To Edit an Existing Highlight the Record and Click Edit or Click Add To Add a New Record
1. Select the Proper IP Address, TCP Port, and Host Header Value
1. Hit OK
1. If you are only hosting one site and this site is the only site bound to port 80 inside of IIS you can simply access the site using the server IP address at http://1.2.3.4

##  How do I manage MIME types for a site in IIS 7?
 
The following article explains how to manage MIME types for a site in IIS 7. A MIME type determines have a specific file extension is to be processed when a page with that extenion is requested in a browser. By default, IIS 7 includes a list amount of MIME types
  
1. Connect to the site using the IIS 7 manager.
1. Select either the domain name or a folder in the domain
1. Under IIS, double click MIME Type
1. Under Actions, click Add
1. Specify the MIME type for the extension
1. Click OK  
  
  
## To edit an existing MIME type, please follow these steps:
 
  
- Select the extension from the list and click Edit.
- Enter the new MIME type information.
- Click OK.
 