---
title: Installation & Upgrade
description: 
published: true
date: 2021-05-15T03:37:30.556Z
tags: 
editor: markdown
dateCreated: 2021-05-15T01:34:12.538Z
---

# Install Microsoft DNS Server on W2k3

- Click Start, point to Settings, and then click Control Panel.
- 
- Double-click Add/Remove Programs.
- 
- Click Add and Remove Windows Components.
- 
- The Windows Components Wizard starts. Click Next.
- 
- Click Networking Services, and then click Details.
- 
- Click to select the Domain Name System (DNS) check box, and then click OK.
- 
- Click OK to start server Setup. The DNS server and tool files are copied to your computer.
- 
- Continue to the next step to configure the DNS server.

# Install Microsoft DNS Server on W2k8

- Login into your Windows Server 2008.
- Click on Start >> Server Manager. This will open up the Server Manager Console, click on the “Roles” listed on the left side panel of your server manager console.
- Click on the “Add Role” and the “Add Roles Wizard” will be displayed. Simply, hit the “Next” button
- Once you hit the “Next” button the “Server Roles” window will appear
- You need to select the “DNS Server” by ticking the check box in-front of it and Hit the Next button.
- Here you will get a DNS Server overview page where you will find some introduction to the DNS Server.
- Hit the “Next” button when you are finish reading it. Once you hit the next button, you will get the Confirmation page of installation.
- Hit the Install button to start the DNS Server installation process. Once you click the install button you will get the Progress window showing initializing installation
- After some time you will get the Installation Results window conveying a message “Installation Succeeded”
- Lastly, hit the “Close” button to escape from the installation window.

# Installing and Configuring Windows Server 2008 SMTP

- Login to the server with administrator
- Open Server Manager Console and under Features select Add Features
- Select SMTP Server option
- Click on Install wait until finish and click close
- Waiting for installation to finish and clicking on Close
- Opening IIS Manager under Administrative Tools -> Internet Information Services 6.0
- Under SMTP Virtual Server second mouse click and properties
- Select Relay under Access Tab
- Select Only the list below and click on Add button
- Enter IP Address 127.0.0.1 for relay
- Sending a manual email through telnet to confirm everything working successfully. Telnet localhost 25 or telnet yourpublicip 25 and make sure you open the specific port on your firewall to be available to public.

# Install and Configure the Email Server in Windows Server 2003

You can install the Email Server by using Add or Remove Windows Components or Manage Your Server. In this tutorial we will use the latter, because it's the quickest way to get this up and running. Manage Your Server is a bit easier to use too, because it will prompt you for the domain you want to use during setup. That will not Add or Remove Windows Components do, and we have to do everything manually.
If it's not open, start Manage Your Server by clicking Start->Programs->Administrative Tools->Manage Your Server.

 

Click on Add or remove a role.

It will start the Configure Your Server Wizard. Read the text and make sure you have connected all the necessary cables and all the other things it says you should do before continuing.

Click Next

The wizard will now detect your network settings. This will take a while depending on how many network connections you have

We now come to the step where we add and remove roles for our server. We will add the Mail Server role. I also suggest that before you click Next, click Read about mail servers because this tutorial is not a complete reference.

Click Mail server (POP3, SMTP)

Click Next

You will now specify the type of authentication and type the email domain name. In this tutorial we will use Windows Authentication

You should of course use your domain name

Click Next

Next step is to confirm the options you have selected

The installation will start, and will also start the Windows Components Wizard. When you get prompted to insert your Windows Server 2003 CD-ROM into your CD-ROM drive, do so. If you didn't get prompted to do that, you maybe already have it in the drive. Hopefully within some minutes you get this screen

You can now see the log, click view the next steps for this role, or click Finish. Do whatever you feel you want to do before continuing.

Click Finish

__________________________

# Install FTP service and configuration on W2k3 server


**Install Internet Information Services and the FTP Service**
Because FTP depends on Microsoft Internet Information Services (IIS), IIS and the FTP Service must be installed on the computer. To install IIS and the FTP Service, follow these steps.

NOTE: In Windows Server 2003, the FTP Service is not installed by default when you install IIS. If you already installed IIS on the computer, you must use the Add or Remove Programs tool in Control Panel to install the FTP Service.

Click Start, point to Control Panel, and then click Add or Remove Programs.
Click Add/Remove Windows Components.
In the Components list, click Application Server, click Internet Information Services (IIS) (but do not select or clear the check box), and then click Details.
Click to select the following check boxes (if they are not already selected):
Common Files
File Transfer Protocol (FTP) Service
Internet Information Services Manager
Click to select the check boxes next to any other IIS-related service or subcomponent that you want to install, and then click OK.
Click Next.
When you are prompted, insert the Windows Server 2003 CD-ROM into the computer's CD-ROM or DVD-ROM drive or provide a path to the location of the files, and then click OK.
Click Finish.
IIS and the FTP service are now installed. You must configure the FTP Service before you can use it.

# Configure The FTP Service

To configure the FTP Service to allow only anonymous connections, follow these steps:

1. Start Internet Information Services Manager or open the IIS snap-in.
1. Expand Server_name, where Server_name is the name of the server.
1. Expand FTP Sites
1. Right-click Default FTP Site, and then click Properties.
1. Click the Security Accounts tab.
1. Click to select the Allow Anonymous Connections check box (if it is not already selected), and then click to select the Allow only anonymous connections check box.
1. 
1. When you click to select the Allow only anonymous connections check box, you configure the FTP Service to allow only anonymous connections. Users cannot log on by using user names and passwords.
1. Click the Home Directory tab.
1. Click to select the Read and Log visits check boxes (if they are not already selected), and then click to clear the Write check box (if it is not already cleared).
1. Click OK.
1. Quit Internet Information Services Manager or close the IIS snap-in.

The FTP server is now configured to accept incoming FTP requests. Copy or move the files that you want to make available to the FTP publishing folder for access. The default folder is drive:\Inetpub\Ftproot, where drive is the drive on which IIS is installed.

# Install & Configure FTP on w2k8 server

- Open Server Manager, go to Roles and click “Add Roles”
- In the Add Role Wizard, select Web Server (IIS) role to install
- Click Next until you reach Select Role Services page, leave the default and check FTP Server, FTP Service and FTP Extensibility at the bottom. Click Next, follow the wizard and finish the role installation.
- Click Next until you reach Select Role Services page, leave the default and check FTP Server, FTP Service and FTP Extensibility at the bottom. Click Next, follow the wizard and finish the role installation.
- Configure Binding and SSL. In our case, we’d like to bind to all unassigned IP addresses and do not use SSL
- Enable Basic Authentication and configure authorization. In our case I’ll start with allowing All users both Read and Write permission as long as all users on the server are password protected.
- Click Finish to finish the configuration.
- Open Windows Firewall with Advanced Security from Start > Administrative Tools, go to Inbound Rules in the left pane, and create a new rule by clicking New Rule in the Action Pane, select Port and click next.
- Apply this rule to TCP port 21, and click Next
- Keep the default configure for the rest of steps to Allow the connection and apply it to all profiles, name the rule and finish the wizard.
- Now the FTP should be up and running, please test the connection to confirm.

# How to Install Perl on W2k3

1) Open IIS 6.0
2) Click on the name of your computer -> click on "Web Service Extensions" and one can view few links. One of them says "Add a new Web service extension...", click on that link.
3) In that window it will ask for the extension name one can put anything, like "CGI script" and under the "Required Files" section put 'C:\Perl\bin\perl.exe "%s" %s' click OK to the notification, click "Set status to allowed" and press ok.
4) Now, one need to go at command prompt and "md c:\inetpub\cgi-bin" [without quote].
5) Now go back to the IIS Manager and right click on Default Web Site highlight "New" in the pop-up menu and click "Virtual Directory..." in the new menu.
6) Click next then as an alias put "cgi-bin" and click next then as a path for the next dialog put in "c:\inetpub\cgi-bin". On the next dialog leave everything checked and checks executes and click next.
7) Click Finish to end the installation wizard.
8) Right-click on cgi-bin directory from default web sites and click on properties.
9) Click Configuration in the lower right-hand area of the dialog and make sure .pl is there (if it isn't, add it the way you see it).

To make the scripts work the line (#!/usr/bin/perl) should now be #!C:\Perl\bin\perl.exe. Any reference to any files should be changed from /home/user etc, to c:/home/user or c:\\home\\users - note the double back-slashes. Now, one should be able to run Perl scripts successfully using Windows Server 2003, and IIS 6.0.

 1) Click on start -> run.
 2) Type tscc.msc and click on OK button.

 3) On the left side you should see that "Connections" is selected, on the right side you should see, under the "Connection" tab, RDP-Tcp. Right click that, and press properties.

 4) Go to the Client Settings tab, and under "Disable the following:" one will see "Audio mapping" checked. Please uncheck it.

5) Click on OK button to complete the process.

# How to install VPN server on W2k3

1. Go to Start > Administrative Tools > Routing and Remote Access.
2. Right-click on server’s icon -> select "Configure and Enable Routing and Remote Access" to start the Setup Wizard
3. Click Next
4. Select "Remote Access (dial-up or VPN)"
5. Click Next.
6. Check the VPN check box and then click next.
7. in the "VPN Connection "window, select the network interface is connected to the Internet and click Next.
8. In the "IP Address Assignment window", there are two options available:
 

    *Automatically Choose this option if you have a DHCP server.
    *From a specified range of addresses Choose the option if the remote clients can only be given an address from a specified pool of addresses.
 

9. Select default value of No, use Routing and Remote Access to authenticate connection requests and click the Next.
10. Click Finish to turn on RRAS and to configure the server as a remote-access server.
 

**Note: One must have to setup RRAS and turn on the service for VPN server**.

# How to set scheduler tasks in W2k3

1) Click on Start -> Control Panel -> Scheduled Task.
2) Click on “Add Scheduled Tasks”.
3) Click on Next to continue.
4) Select scheduler task file or program for which one need to set it.
5) Click on Next.
6) Provide scheduler name and select the radio button to fix scheduler run time. Options are:
    Daily
    Weekly
    Monthly
    One Time Only
    When my Computer Stats
    When I log on
7) Click on Next.
8) Select the time and scheduler start date.
9) Enter scheduler username and password.
10) Click on Finish

#  How to set scheduler tasks in W2k8

Log into your server through Terminal Services or Remote Desktop Connection
Navigate to Start > All Programs > Administrative Tools > Server Manager. This brings you to the Server Manager interface
Drill down to Configuration > Task Scheduler
On the right hand side of the interface, click Create Basic Task… Give the task a name and description. Click Next
Select the radio button for how often the task should run: Daily, Weekly, Monthly, one time only, when the computer starts, when I log in, or when a specific event is logged. Click Next
Select a start time, how often to perform the task, and an end time. Click Next
Configure the task to Start a Program, Send an e-mail, or display a message by selecting the appropriate radio button. Click Next
Browse to the program or script and enter in any arguments or paths to start in. For example to run a command prompt, enter in C:\Windows\System32\cmd.exe. Click Next
Select the checkbox for Open the Properties dialog for this task when I click Finish if you wish to configure the task further. Click Finish
The Advanced Properties window will appear. Configure the task further to your liking by adding comments to the task, telling the task when to run (only if logged in or otherwise), deleting the task after its run if it's scheduled to not run infinitely, to reschedule the task if it is missed, and so forth. After doing so, the task is setup and will run if configured proper



