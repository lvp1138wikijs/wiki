---
title: IIS 6.0 How Tos
description: 
published: true
date: 2021-12-20T20:31:46.769Z
tags: 
editor: markdown
dateCreated: 2021-12-20T20:19:41.948Z
---

# IIS 6.0 How Tos


## How to Enable logging for IIS SMTP and Interpret the Logs

1) Connect your server via Remote Desktop and login with Administrator user

2) Open IIS (Start > Run >inetmgr <enter> )

3) Right Click Default SMTP Virtual Server and Select Properties

4) Click Enable logging

5) the next windows will show where the logs are located

6) Enable all fields so the maximum amount of information is logged

7) Once you've enabled logging you can now check your mail logs which should be in C:\WINDOWS\system32\LogFiles\SMTPSVC1

8) The file will contain a header with the following fields for each transaction

#Software: Microsoft Internet Information Services 6.0

#Version: 1.0

#Date: 2010-01-29 21:16:20

#Fields: time c-ip cs-method cs-uri-stem sc-status

Understanding the SMTP codes

s - Server,

sc -Server to Client.

c - Client

For example sc-bytes means the number of bytes sent by the server to the client.
  

## How to Enable Directory Browsing in IIS 6
  
 If you wish to share files through a web interface without creating a web interface to do it you can simply enable directory browsing within IIS for the particular folder / site.
  
1. Connect to your server via Remote Desktop.
1. 
1. Open IIS by clicking Start, select Run and type inetmgr press enter
1. Find your site in IIS, right click and select Properties either on the site or a folder you wish to use directory browsing with.
1. 
1. Click the Home Directory tab and check the box next to Directory Browsing.
1. Click Apply or OK and directory browsing is now enabled.
  
  
## How to Enable HTTP Compression for a website in IIS 6

Enabling HTTP Compression on an IIS website will improve bandwidth utilization and speed up overall performance.

1. Connect to your server via Remote Desktop.
1. Open IIS, click Start -> Administrative Tools -> IIS Manager
1. Expand the local computer, right click on Websites folder and select properties
1. Click on the Service tab,
1. Under the HTTP Compression section select the Compress application files check box for dynamic files and select the Compress static files check box for static files.
1. Under the Maximum Temporary Directory Size section you can set the size if you wish by clicking the radio button, Limit to(in megabytes)Click 
1. Click OK and you are done.
  
##   How to Enable and Disable ASP in IIS 6

You can enable or disable ASP in IIS via Remote Desktop.

1. Connect to your server via Remote Desktop.
1. Open IIS; click Start, select Administrative Tools and click on your Internet Information Service (IIS) Manager.
1. Click and expand your local computer and select Web Service Extension.
1. Select Active Server Pages from the middle pane and click the Allow button.
1. ASP is now enabled on your IIS 6.0 server
  
  
## How to Enable and Disable Indexing Service in IIS 6
  
You can enable Indexing Service in IIS via Remote Desktop.

1. Connect to your server via Remote Desktop.
1. Open IIS; click Start, select Administrative Tools and click on your Internet Information Service (IIS) Manager.
1. Click and expand your local computer and select Web Service Extension.
1. Select Indexing Service from the middle pane and click the Allow button.
1. Indexing Service is enabled.
  
## How to Install Perl/CGI in IIS 6
  
How to install and setup PERL/CGI on Windows 2003 and IIS 6 

1. Connect to your server via Remote Desktop.
1. Download and install ActivePerl from ActiveState http://www.activestate.com/
1. Open IIS; click Start, select Administrative Tools and click on your Internet Information Service (IIS) Manager.
1. Click and expand your local computer and select Web Service Extension.
1. Click on the Add a new Web service extension right next to the first green arrow
1. For the Extension name, type CGI script , click the Add button and type, C:\Perl\bin\perl.exe "%s" %s
1. At the notification, click OK
1. Check the box that says Set status to allowed and press OK
1. Open the command prompt, How do I open a command prompt?
1. Create a directory within \inetpub called cgi-bin, type md c:\inetpub\cgi-bin
1. In your IIS Manager right click on Default Web Site, select New, and click Virtual Directory.
1. Click Next, for the Alias name type cgi-bin and click Next.
1. For the Path navigate to or type out c:\inetpub\cgi-bin and click Next
1. Make sure Read, Run scripts and Execute are checked and click Next and Finish
1. Right click on the Virtual Directory, cgi-bin and select Properties
1. Click the Configuration button
1. Click Add and add .pl the way you see it in the picture below using the verbs, GET,HEAD,POST,DEBUG
1. Click OK and you are done. 
  
## How to set up 301 Redirect in IIS 6

  
You can do a permanent redirect from an IIS website to a different URL.

1. Connect to your server via Remote Desktop.
1. Open IIS; click Start -> Administrative Tools -> IIS Manager.
1. Expand the local computer, expand Web Sites, and right click on the website and select Properties
1. Select the Home Directory tab from the menu.
1. Select A redirection to a URL radio button
1. In the Redirect to: line, type your new url
Select the A permanent redirection for this resource check box and click OK

  
## How to Increase File Upload Size in ASP & ASP.NET
  
There is no GUI option in Server 2003 to increase the ASP upload size limit. This guide will show you how this can be accomplished via the command line.
  
The default server size is 204,800 bytes (200k).

- Connect to your server via Remote Desktop.
- Open the command prompt.
- At the command prompt type "cd C:\Inetpub\AdminScripts" and press enter:
- Type the following command and press enter to check the upload limit:
- cscript adsutil.vbs get w3svc/ASPMaxRequestEntityAllowed
- To change the value to say 100mb, run the following command:
- cscript adsutil.vbs set w3svc/AspMaxRequestEntityAllowed 104857600
- Run the IIS restart command by typing: iisreset /restart and you are done  
  
##   How to Preview your site on a Windows Server with IIS 6 Host Headers
  
Let's make an example per say that your server IP address is 1.2.3.4 and your domain is mydomain.com. You are working on the site and want to test the site on your server at serverpoint.com however you are not ready to update DNS just yet.

For this tutorial it is important to under host headers and how to set them inside of IIS
  
**Modify Host Header Information in IIS6**
 
 1) Start > Run > inetmgr <enter>

2) Expand Web Sites

3) Right Click on Web Site to be Adjusted and Choose Properties

4) On the Web Site tab click Advanced

5) To Edit an Existing Record Double Click the Record or Click Add To Add a New Record

6) Select the Proper IP Address, TCP Port, and Host Header Value

7) Hit OK, OK, Apply, OK and You are Done.
  
## How to Backup the Metabase in IIS 6
 
  
This guide will show you how to backup your IIS Metabase before making any changes to the Metabase XML file.

1. Connect to your server via Remote Desktop.
1. Open IIS; click Start -> Administrative Tools -> IIS Manager
1. Right Click on your local computer, select All Tasks and click Backup/Restore Configuration...
1. Click the Create Backup button.
1. Type in a name and you can even password protect it, click OK.
1. You are finished. You can restore the backup you made selecting the backup and clicking Restore
  
## How do I add a new file extension or MIME type in IIS6
  
 The following article explains how to create a MIME type for a new file extension. MIME types are created in IIS and allow different file extensions to work in a Web browser. For example, if you wish to use Web pages with the .js file extension, you may need to add the application/x-javascript mime type to IIS.
  
- Log into your server through Remote Desktop Connection 
- Click Start, Programs, Administrative Tools, and select Internet Information Services (IIS) Manager
- Expand local computer and expand Web Sites
- Right click the appropriate website entry and select Properties
- On the HTTP Headers tab click MIME Types
- Click New  
  
Enter the appropriate information:

- Extension - the file type extension
- MIME type - the type of file this extension refers to
- Click Ok
  
You may need to restart the IIS service for the MIME type to begin working. To restart the IIS service, please follow these steps:

- Click Start
- Select Programs
- Click Command Prompt
- Type iisreset and press Enter
  
Note: restarting the IIS service will temporarily suspend the web service and prevent websites from working. The reset should only take around 10 - 30 seconds to complete
  
## How to Configure SSL Host Headers in IIS 6
  
  
This article discusses how to use only one IP address and have multiple SSL installs on the single IP address. Typically each SSL install requires a dedicated IP address, that of which is not assigned to any other site in IIS, to work. This article will provide a workaround for that scenario and only applies to Dedicated or Virtual Machines running Windows with IIS6.
  
**To configure an SSL in IIS6 with SSL host headers, follow the steps below**:

- Log into the server via Remote Desktop.  
- Navigate to IIS (Internet Information Services) in the Remote Desktop session by either double-clicking the IIS icon on the desktop or going to Start > Run > and typing inetmgr.
- Expand the tree within IIS to view the sites under the Web Sites heading.  Right-click the site in question and choose Properties.  Click the Advanced button under the Web Site tab and ensure that the host header values are set for the domain. If the host header values are correct, click OK.  Otherwise edit the values and go back to the main IIS interface when done.
- Also ensure that the SSL to use is already installed in IIS .
- Next, configure the SecureBindings metabase property on each of the sites so it contains the host header.  To do this, open a command prompt by going to Start > Run > and typing cmd.
- Within the command prompt dialog window, change directories to C:\Inetpub\AdminScripts by typing cd C:\Inetpub\AdminScripts.  Contained in this folder should be a file named adsutil.vbs.  If not, change to the directory where that file is located.
- Run the following command at the prompt entering in the appropriate information related to the sites where <site identifier> is the site identifier within IIS and <host header> is the value of the host header for the site in IIS:
- cscript.exe adsutil.vbs set /w3svc/<site identifier>/SecureBindings ":443:<host header>"
- In the case above, if domain.com and domain2.com are to use the same SSL, the commands to run would be:
- Run this command for each site that needs to be use the certificate.  Each site will then use the certificate that was installed on the first site with that IP address.  
  
  
## How to Enable Server Side Includes For IIS 6
  
  
This article will go over on how to add the Server Side Include option for IIS 6. Without this enabled your IIS instance will not be able to run SHTML pages.
  
1. Log into your Windows server by accessing it with Remote Desktop Connection.
1. Navigate to your Internet Information Server (IIS6) by either typing "inetmgr" from the command prompt or by going to Start > Administrative Tools > Internet Information Services (IIS) Manager.
1. In the IIS Manager, expand the server tree and once that is expanded, click on the "Web Service Extensions" tab. Here you will see the extensions that are currently installed. You will see that "Server Side Includes" are set to "Prohibited". You will need to highlight this and then click on the "Allow" button. This will enable the "Server Side Includes". Anything that depends on this extension will now work.  
  
  
## Changing the Site ID In IIS 6
  
By default IIS will assign a random Site ID to a website and does not provide any options on changing them. This article will explain how to manually make the change to a domain in IIS and allow you to change the Site ID to one that you specify.
  
1. Log into your Windows 2003 server with Remote Desktop Connection.
1. Since Windows does not provide a GUI for changing the Site ID, this will all take place at the command prompt, so you will need to drop into a command prompt by typing "Cmd" at the run prompt.
1. Now that you are in the Windows Cmd prompt, which looks like MS-DOS. Before you make any changes, you will need to take note of the Site ID of the website / domain that you want to change. To do this, open up the IIS manager and view the Site ID. For this example we will say we are dealing with the site ID of 64575 and we want to change it to the Site ID of 27.
1. To change the Site ID, you must first stop the domain / website by typing the following command:
1. CSCRIPT %SYSTEMDRIVE%\Inetpub\AdminScripts\adsutil.vbs STOP_SERVER W3SVC/ 64575
1. Now that the domain / website is stopped we need to tell Windows to change the existing Site ID to your new Site ID. To do this, we now need to type the following command:
1. CSCRIPT %SYSTEMDRIVE%\Inetpub\AdminScripts\adsutil.vbs MOVE W3SVC/ 64575 W3SVC/ 27
1. The existing Site ID has now been changed, so now we just need to start the domain / website by running the following:
1. CSCRIPT %SYSTEMDRIVE%\Inetpub\AdminScripts\adsutil.vbs START_SERVER W3SVC/ 27
1. If you still have the IIS manager open, close it and then reopen it. You will see that the Site ID has now changed to the new ID you provided  
  
  
## How to Recycle Application Pools in IIS6 & IIS7
  
  
Recycling an application pool causes the WWW service to shut down all running worker processes that are serving the application pool, and then start new worker processes.

1) Login to your server with RDP and administrator user

2) Launch IIS, Start > Run > inetmgr
  
## Instructions for IIS6
 
- Expand the Computer Name
- Expand Application Pools
- Right Click on Application Pool you want to recycle
- Click Recycle  
  
## Instructions for IIS7

1. Expand the Computer Name
1. Select Application Pools
1. Right Click on Application Pool you want to recycle
1. Click Recycle
   