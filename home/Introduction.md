---
title: Introduction
description: 
published: true
date: 2021-04-09T14:25:09.877Z
tags: 
editor: markdown
dateCreated: 2021-02-16T16:33:09.082Z
---

# Header
- Welcome
- Timings
- Basic Skills
- Know the company
- Setting up your system
- Opening a Shared Hosting Account
- CONTROL PANEL
- APLUS WEBMAIL
- Setting up SSH Tunnelling
- Script Installation
- Welcome to Our Team

**Welcome**

We are excited to welcome you as a new member of our family at ServerPoint.Com. A+ Hosting Inc. DBA ServerPoint.Com is a company that produces its best due to the creativity, energy, and dedication of members like you, who help us maintain the excellence that characterizes us. Together, we will be able to reach our goals through the dynamic and progressive environment.

This document provides information about the basic things you should know.

Please feel free to ask any questions you may have. Your managers and colleagues will be glad to assist you in every way they can. Prepare yourself for a world of challenges, excitement, adventures, and success.

**Timings**

Your temporary timings during the first weeks of training are not permanent, please be aware that your hours will be changed before you finish your first month. When referring to hours, we always use PST time zone, please be sure you make the necessary conversions.

**Basic Skills**

There are some basic skills that you are supposed to be familiar with and proficient in order to work for us. The following link contains a list of the most important but basic skills required in order to be able to solve issues related to domain propagation.

Basic Skills

**Know the company**

The first step is to familiarise yourself with the company. In order to do that, you should make sure you read the entire website 

https://www.serverpoint.com
 https://www.colossuscloud.com
 
- Our Locations
- Our Services and Programs
- Collect your Queries/Questions

**Be sure to put special attention to all the major product and services we offer**:

Web Hosting http://www.serverpoint.com/en/web-hosting/

Dedicated Servers http://www.serverpoint.com/en/dedicated-server/

Virtual Dedicated Server (VPS) https://www.colossuscloud.com/vps-hosting/

Managed Dedicated Server Hosting (Details about Backups and other services) 

- Try placing orders (for Shared/Dedicated and VPS)
- Check for the payment methods
- Come-up with your questions

**Other critical areas that you must be familiar with are**:

- Knowledgebase Section - https://secure.serverpoint.com/tickets/index.php?/Knowledgebase/List
- Video Tutorials - http://www.serverpoint.com/en/tutorials.phtml  (OLD)
- Policies - http://www.serverpoint.com/en/privacy.pdf   (will share others once you get the access)
- (Webmail, Client Portal etc can be accessed from here) - https://www.serverpointapps.com/

- Be sure you send a message to the ticket system: http://www.serverpoint.com/en/contact-our-staff.phtml

**Setting up your system**

Make sure you have following applications installed

**Skype**

Create a new skype account and provide the username information to your Senior Admin. Once the information is received we will send you the contact list information you need to add to your skype. Make sure that you have logged in to skype during the shift since it will be used as one of the main communication tools. Be sure your skype is only using for business communication purpose only.

**Text Pad**

TextPad is a powerful, general purpose editor for plain text files.
Easy to use, with all the features a power user requires.You can download and install the latest version from this URL: http://www.textpad.com/download/index.html
You can refer the installation documents from the URL: http://www.textpad.com/download/index.html#instructions
You should only use Text Pad to edit any text file or queries for your work

After installation and signup

**WinSCP**

WinSCP is an open source SFTP client and FTP client for Windows. Its main function is the secure file transfer between a local and a remote computer.

You can download and install the latest version from the following URL: http://winscp.net/eng/download.php

You can refer the installation documents from the URL: http://winscp.net/eng/docs/installation

**Open office**

Openoffice is the software we use to create documents or read business documents.

**efax viewer**

We'reusingefaxviewerto open faxes received from the customers.

You can download it using the following link: http://a248.g.akamai.net/f/248/528/7d/images.j2.com/twa/US/msgrplus.exe

**Kayako Desktop app for chat support**

DO CHAT SUPPORT ONLY WHEN YOU ARE CLEAR TO DO SO.

You can download http://hotfix.kayako.com/latest.php?product=kd&platform=win32&buildtype=stable

URL is: https://secure.serverpoint.com/tickets

Use the same login details as your kayako control panel

**Mozilla Thunderbird**

Mozilla Thunderbird is a free, open source, cross-platform email and news client developed by the Mozilla Foundation.

You can use thunderbird to configure official email address.

URL: http://www.mozilla.org/en-US/thunderbird/

**TrueCrypt**

Truecrypt is aopen source disk encryption software and it is recommended to use it to store sensitive data like passwords.

If you are using simple notepad file to store your username/password for internal usage at Serverpoint.com then you must use Truecrypt to create disk encryption. Click here to read how you can use TrueCrypt.

**Opening a Shared Hosting Account**

Opening a shared hosting account will get you get more familiar with the account creation, plan, rates, services offered and our in-house control panel.

Once the account is approved by our staff, a welcome email will be sent to the address you specified at the time of account creation. Log in to the control panel and go through each section to get familiar with it.

**CONTROL PANEL**

Once your account is created, you will receive a welcome email which contains the link to our control panel along with your new username and password. You can access the control panel in the followingURL: https://www.serverpointapps.com/ , click on “Client Portal”

Be sure you carefully read and understand all the features included in the control panel. Remember features vary depending on the type of account that you have.

**Difference between main and resold account**

The owner of resold accounts the main account user in other words, all resold accounts belong to their reseller. The main user can cancel, suspend, downgrade/upgrade the resold account.

control panel for both accounts: https://www.serverpointapps.com/

There is no accounting and reseller section in the resold control panel since the main account is fully responsible for all that.


**WEBMAIL**

You can send and read emails using our webmail interface.

You can access our webmail interface at the following URL: https://www.serverpointapps.com/webmail

Enter the username for the pop3 account in the first box.In second box enter your domains name. In the last box enter password for the user. Then hit on the login button.

**Setting up SSH Tunnelling**

**How to find IP of your email server**

We have 4 email servers, for now, therefore you need to find out what email server is being used for your domain. To find, open putting and run host command for your domain, see example below

```
-sh-4.2$ host serverpointsupport.com
serverpointsupport.com has address 64.235.42.4
serverpointsupport.com mail is handled by 10 email-mx.serverpointsupport.com.
-sh-4.2$ host email-mx.serverpointsupport.com.
email-mx.serverpointsupport.com has address 72.18.207.140
-sh-4.2$
```

So this shows 72.18.207.140 is your email server, and you can replace it in below explanation of setting up ssh tunnel.


**Windows Platform**

- Open Putty, in the left panel, expand the Connection → SSH → Select Tunnels and add new forwarded port

- source port: 1110
- Destination: 72.18.207.139:110

Leave other settings unchanged. Click Add to Save it. Now add another port

- source port: 125
- Destination: 72.18.207.139:25
- Click Add to Save it.

Now login to your account at ServerPoint and these ports will be automatically forwarded to localhost. It is advised you save it as a session in Putty so you can load the configuration every time you open Putty.

**Note that Destination has IP/Hostname of mail server your account resides on. It may differ from IP mentioned above**.

Refer the following URL for more details: http://www.jfitz.com/tips/putty_config.html

**Linux Platform**

ssh username@domainname.com -L 125:72.18.207.139:25 -L 1110:72.18.207.139:110

The above command will open ports on 125 and 1110 respectively in Linux

**Email Client**

Once tunneling is setup confirm this by using telnet command

telnet localhost 1110
telnet localhost 125
If it is successful, update the email client to use new ports. In email account config, update following info

Mail Server (Incoming/Outgoing): localhost
Incoming Port: 1110
Outgoing Port: 125
UserName : username@domainname.com

**Script Installation**

As part of your training, you should install and configure a series of scripts. You must familiar with the installation and configuration so that you can support to our customers.

Login to Client Portal from Serverpointapps.com >> Then Menu >> Web Apps Installer. Select the application you want to install, then click on Install This Application button.

**Welcome to Our Team**

I hope we can work together as a team for a very long time. Wish you good luck and success.

