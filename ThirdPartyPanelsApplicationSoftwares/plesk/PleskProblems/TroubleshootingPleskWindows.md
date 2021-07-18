---
title: Troubleshooting Plesk Windows
description: 
published: true
date: 2021-07-18T05:41:42.558Z
tags: 
editor: markdown
dateCreated: 2021-07-18T05:41:42.558Z
---

## MailEnable: Message delivery has been delayed - Windows

Message is waiting at domain.com for delivery to hotmail.com. 

**Fix**:

1. Connect to your VPS via Remote Desktop.
1. Go to My Computer→ C drive→Program Files→SWSoft→Plesk→MailEnable→bin click mailenable.msc (Path can vary according to plesk installation)
1. In the console which opens up, go to Servers > Localhost > Connectors> SMTP
1. Right click on SMTP > Properties
1. Give your server IP address in the DNS address field and your domain name in the Domain field. Click on Apply.
1. Then restart MailEnable (SMTP) service


## How to reset mysql password in windows plesk

```
  Login to plesk and in Server-> Databases -> MySQL tab -> Click Mysql server and there you can find an option to reset mysql password.
```

Note: Plesk for windows use 2 mysql instances. One is system instance, You should not use it. And it dont run on default mysql port. The system instance run from c:\swsoft\plesk\mysql And user instance run from c:\swsoft\plesk\databases\mysql Both have different my.ini files in data directory of each of above directory

## How to delete mail queue in Windows Plesk

1. Log in to Windows via RDP, Click Start Button and find Mail Enable Administrator
1. Click on Queue»Outbound
1. Click Mail Queue
1. Right Click and Delete.

## MySql problems

1. Log in to Plesk. Click on “Database Servers” under “Services”.
1. Check if there is an exclamation mark next to “Local MySQL server”. When you hover over it, it will give you a message like “Plesk could not contact this server”. This usually means the service is down.
1. Click Start → Control Panel → Administrative Tools → Computer Management
1. Once there, click on “Services” on the left. That will show a list of all services running on the server, including MySQL.
1. Scroll down to “MySQL Server” and right click on it. If it shows you the option to “Start” it, it means the service is down. If not, it will show you options to “Restart” and “Shut down”. You can also try restarting if it ever happens again.
1. Also, check the Properties of the MySQL server, and specially check the “Recovery” tab. You can configure Windows to automatically restart the service if it fails. I will leave that decision to you.
 

