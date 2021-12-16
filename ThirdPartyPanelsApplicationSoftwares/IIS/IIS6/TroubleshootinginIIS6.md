---
title: Troubleshooting in IIS 6.0
description: 
published: true
date: 2021-12-16T18:49:33.873Z
tags: 
editor: markdown
dateCreated: 2021-12-16T18:49:33.873Z
---

# Troubleshooting in IIS 6.0


###  All requests with /bin in the URL are rejected and return a 404 error

This occurs when IIS 6.0 and ASP.NET are both installed. In order to take a more proactive stance against malicious users and attackers, the ASP.NET ISAPI filter, aspnet_filter.dll, blocks incoming request containing /bin in the URL. This behavior occurs server-wide, regardless whether the request is for static or dynamic content.

The preferred solution to this issue is to modify the path to content on the server so that /bin is not necessary in any request.

If the content URL cannot be modified, an alternative solution is to set a registry key that stops the ASP .NET ISAPI filter from filtering requests containing /bin in the URL. This is a server-wide setting.

**To disable /bin filtering **

1. Start Registry Editor and navigate to the 
1. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\ key.

1. In the details pane, right-click, point to New, and click DWORD Value.
 
1. In the Name box, type the following: StopBinFiltering.

1. Double-click the StopBinFiltering value, and in the Value data box type 1.

1. Click OK, and then close Registry Editor.

1. To reenable /bin filtering, set the StopBinFiltering value to 0.


### Worker process recycling drops application session state

By default, Worker Processes recycle after a preconfigured amount of time. If your ASP applications are not designed to store session state while a worker process is recycled, then session state in that ASP application can be lost. To remedy this problem, you can either store session state in a database or disable worker process recycling.

**To disable worker process recycling**

1. In IIS Manager, expand the local computer, expand Application Pools, right-click the application pool, and then click Properties.

1. On the Recycling tab, clear the Recycle worker processes (in minutes) check box.

1. Click OK.

### Server-side include directives (#include) return 404 error (for .stm files) or 0131 error (for .asp files)

If your ASP page uses the #include server-side include directive and the ".." notation to refer to a parent directory, the directive will return an error unless you have reconfigured the AspEnableParentPaths Metabase Property. This property is set to false by default.

**To enable parent paths through IIS Manager** 

1. In IIS Manager, expand the local computer, right-click the starting-point directory of the application you want to configure, and then click Properties.

1. Click the Directory tab, and then click Configuration.

1. Click the Options tab.

1. In the Application configuration section, select the Enable parent paths check box.
 
1. Click OK.

### Requests for dynamic content return 404 error

To help minimize the attack surface of the server, IIS 6.0 is not installed on Windows Server 2003 by default. When you first install IIS 6.0, it is locked down — which means that only request handling for static Web pages is enabled, and only the World Wide Web Publishing Service (WWW service) is installed. None of the features that sit on top of IIS are turned on, including ASP, ASP.NET, CGI scripting, FrontPage® 2002 Server Extensions from Microsoft, and WebDAV publishing. If you do not enable this functionality after installing IIS, by default on this denial, IIS returns a generic 404 custom error page to prevent disclosure of configuration information. IIS also writes the 404 error with the substatus code of 2 (404.2) in the W3C Extended log files, by default.

**To enable or disable a Web service extension** 

1. In IIS Manager, expand the local computer, and then click Web Service Extensions.

1. In the details pane, click the Web service extension that you want to enable or disable, and then do one of the following:

     To enable a disabled Web service extension, click Allow, and then click OK. 
     To disable an enabled Web service extension, click Prohibit, and then click OK.
     
### Clients cannot connect to server
     
If you have enabled the firewall in its default configuration after installing a member of the Windows Server 2003 family and before installing IIS, clients will not be able to connect to your server. The following procedure configures ICF to allow clients to initiate Web and other IIS-related connections to your server.

**To configure Internet Connection Firewall for IIS**

1. From the Start menu, click Control Panel.

1. Double-click Network Connections.

1. Right-click Local Area Connection, and click Properties.
 
1. Click the Advanced tab.
 
1. If you do not want to use the ICF, make sure the Protect my computer and network by limiting or preventing access to this computer from the Internet check box isn't available, and click OK.

1. If you do want to use the ICF, make sure the Protect my computer and network by limiting or preventing access to this computer from the Internet check box is enabled, and click Settings.

1. On the Services tab, enable a service to which you want to allow access to clients.

1. In the Service Settings dialog box that appears after enabling a service, do one of the following:

  - If you are enabling a service on the same computer you are working, the correct computer name is already filled in. Click OK.
  - If you are enabling a service on a different computer on your network, type the name or IP address of the computer hosting the service you are enabling, and clickOK.
  
- Repeat steps 7 and 8 until all the services you want accessible to clients are enabled.


### Clients browsing to a Web site receive HTTP 403.4 - Forbidden: SSL is required to view this resource error, but the Web site is not configured to use SSL

It is possible that the Web site configuration has been altered to require SSL, although no certificate has been associated with the Web site. This might happen because the Edit button on the Directory Security tab is available although no certificate is associated with the Web site. The Edit button allows changes to be made to the site's SSL configuration even if a certificate has been removed.

To correct this problem, change the Web site configuration to not require SSL.

**To remove SSL from a Web site by using IIS Manager**

1. In IIS Manager, right-click the Web site whose SSL configuration you want to change, and then click Properties.

1. On the Directory Security tab, in the Secure Communications area, click Edit.

1. Clear the Require Secure Channel (SSL) check box, and then click OK.

**To remove SSL from a Web site by using adsutil.vbs**

1. Click Start, click Run, type cmd, and then click OK.

1. Change to the inetpub\adminscripts directory.
 
1. At the command prompt, type the following command for the Web site whose SSL configuration you want to change, substituting # with the Web site identifier: 
1. cscript adsutil.vbs set w3svc/ # /AccessSSL False


### Determining the Intermediate Root CA Version on a Web Server

**To determine the Intermediate Root CA version on a Web server**

- From the Start menu, click Run, type mmc, and then click OK.
- On the File menu, click Add/Remove Snap-in.
- On the Add/Remove Snap-in dialog box, click Add, select Certificates from the snap-in list, and then click Add.
- Choose the Computer account option and then click Next.
- Select Local Computer (the computer this console is running on), and then click OK.
- Click Close, and then click OK.
- In the console window, expand Certificates, and then expand Intermediate Certificate Authorities.
- Click the Certificates folder.
- In the Issued To column, locate the certificate with "Geo Trust-xxxxxxxxx" as the certificate name.
- Right-click the certificate, and then click Open
   - If the certificate has expired, the following message is     displayed on the General tab:
   -"This certificate has expired or is not yet valid."
   - If the certificate is current, the following message is       displayed on the General tab:
   - "This certificate is intended for the following       purposes:"
    and lists the purposes for which the certificate is to be     used.
    
- Note the Valid from date to date range, and then click OK.


### Clients receive 403.16 when logging on to a Web server over an SSL connection


**To resolve this issue, take the following steps**: 

1. Determine the version of the Intermediate Root CA that is currently active on your Web server. For more information, see Determining the Intermediate Root CA Version on a Web Server.

1. If necessary, obtain the current Intermediate CA certificate from the VeriSign Web site. On the VeriSign Web site, search for the Microsoft IIS 5.0 heading, and then click Get Intermediate CA Here (If Required) in Step 1.

1. Follow the instructions at the VeriSign Web site to perform the following tasks:

     - Remove the expired Intermediate Root CA from your Web server.
     - Install the current Intermediate Root CA on your Web server.
     - Reboot your Web server and test the SSL connection.

  