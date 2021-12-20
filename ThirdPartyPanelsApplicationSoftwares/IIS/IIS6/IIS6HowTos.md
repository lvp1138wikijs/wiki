---
title: IIS 6.0 How Tos
description: 
published: true
date: 2021-12-20T20:19:41.948Z
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
  
  
