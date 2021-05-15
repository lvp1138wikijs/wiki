---
title: Installation & Upgrade
description: 
published: true
date: 2021-05-15T01:34:12.538Z
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

