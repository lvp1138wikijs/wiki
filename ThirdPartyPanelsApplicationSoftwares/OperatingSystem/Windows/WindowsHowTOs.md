---
title: Windows How TOs
description: 
published: true
date: 2021-05-15T05:19:16.628Z
tags: 
editor: markdown
dateCreated: 2021-05-15T05:19:16.628Z
---

# How to Remotely enable or disable Remote Desktop on a Windows Server

Please note that editing the registry is very risky, so be sure you have a verified backup before saving any changes in your registry.

**Edit Remote Registry via RegEdit**

Opening the fDenyTSConnections value through a remote registry is done with administrative permissions via Regedit and selecting the Connect Network Registry option from the File menu.

**Edit the registry**

The HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server\fDenyTSConnections value is set to 1 by default to disable remote desktop; editing the value remotely to 0 will enable remote desktop on the next reboot.

**Reboot**

You can make a reboot happen immediately with either the shutdown command or the Restart-Computer PowerShell command.


## How to Allow More than One Session per User in 2008 R2

In previous versions of Windows Server, to allow the same user to have more than one remote session to the server you would go:
Computer Configuration\Administrative Templates\Windows Components\Terminal Services\Terminal Server\Connections node of the Local Group Policy Editor

But in 2008 R2 you'll not find this under local policies. Instead, type "Remote Desktop Session Host Configuration" in the start menu, and there you can change the 'Restrict each user to a single session' to 'no'.

 

You'll find it under Computer Configuration \ Administrative Templates\Windows Components\Remote Desktop Services\Remote Desktop Session Host \ Connections >> Restrict Remote Desktop Services users to a single Remote Desktops Services session


## How to Remotely change local admin passwords

1) Download the pspasswd tool from Microsoft.

Go to http://technet.microsoft.com/en-us/sysinternals

Copy the pspasswd.exe to the:

2) Copy the pspasswd.exe to the:

c:\windows\system32\

directory on your PC or server.
3) Create a file called “Machinelist.txt” with PC names you wish to change the local admin passwords on; one PC per line.

4) Create a batch file with code similar to this:
pspasswd.exe @machinelist.txt -u domain\administrator -p domainpassword administrator newpassword

echo "Complete"

pause

 5) Edit the batch file with the correct credentials and the new password information

 6) Make sure the machines are online and then run the script. You need to use an account with domain administrator rights for the –u and –p parameters in order for this to run correctly.

## How to Find Who is Logged onto a Server

1).Run on current system

from the command prompt end "query user" or "quser" for short

    
2).Run on a remote system

from the command prompt end "query user /server:SERVERNAME" or "quser /server:SERVERNAME" for short

## Get around "terminal server has exceeded maximum # off allowed connections" error


1) From the command line of another server on the same network run the following command at the CMD prompt.

net use /user:[username] \\servername\share

so if we had a user bob, server sue, and share of www here is what the command would be

net use/user:test \\sue\www (you can also use the ip instead of netbios name)
    
2) now you will need to query the remote session on the other server.

from the CMD prompt type

query session /server:servername
    
3) Now we know the ID of the hung session. We can use that in the next step, which is using the reset command to log off that user.

from the CMD prompt

reset session [1] /server:servername

lets say session 5 is hung on our server bob

reset session 5 /server:test

## How to migrate IIS6 to IIS7

1) To start here are the links to some of the websites I used.
http://learn.iis.net/page.aspx/427/migrate-a-web-site-from-iis-60-to-iis-7/
http://technet.microsoft.com/en-us/library/cc627317.aspx
Now there are some changes that have happened with the software I will try to list those as I come to them.

2) First we had to download the MS Deploy software from Microsoft.
Location.
Seems Microsoft changed where the files were located. Thank you DaveyBoy
Here is the new location.
http://www.iis.net/downloads/microsoft/web-deploy

Installed the 86 on the old server and the 64 on the new.

(this is based on what verison of windows server you have installed... is there anything but 64 bit any more... i mean really)

3) To install MS Deploy on the source IIS 6.0 Web server:
1. Visit the x86 or x64 link in Table 1 and click Download.
2. On the File Download dialog box, click Run.
3. On the Internet Explorer - Security Warning dialog box, click Run.
4. On the Welcome to the Microsoft Web Deployment Tool Setup Wizard page, click Next.
5. On the End-User License Agreement page, click the I accept the terms in the license agreement box, and then click Next.
6. On the Choose Setup Type page, click Custom.
7. On the Custom Setup page, click the Installs the remote agent service down arrow, select Will be installed on local hard drive, and then click Next.
8. Click Install.
9. Click Finish.
10. In Computer Management, under Services, verify that the Microsoft Web Deployment Agent Service is started.

To install MS Deploy on the destination IIS 7.0 Web server:
1. Perform steps 1 through 5 in the previous procedure.
2. On the Choose Setup Type page, click Typical.
3. Click Install.
4. Click Finish.

4) Now we don’t want to take the case of messing up our new server without being able to recover. For this we create a backup with Appcmd. To use appcmd you have to be in the right directory. Which is C:\windows\system32\inetsrv>
Once you have the command line to that directory you will run this line. (just cut and paste)

To create a backup by using appcmd.exe
At the command prompt, type

appcmd add backup "PreMigration"

and press Enter.
To list all existing backups by using appcmd.exe
At the command prompt, type

appcmd list backup

and press Enter.
To restore a backup by using appcmd.exe
At the command prompt, type

appcmd restore backup "PreMigration"

and press Enter.


5) Next you have to check for dependencies which you can use MS Deploy for. You need to go to start and programs, then IIS 7.0 Extensions. There will be a Web Deploy Command Line. All it really does it open the command line to the correct directory for you. Which is c:\Program Files\IIS\Microsoft Web Deploy>
At this command line we will input
msdeploy –verb:getDependencies –source:metakey=lm/w3svc/(site number)
I will list the site numbers. You can find them by going to IIS services on the new either server and looking at the sites. They will have an ID that is listed with them. I will list them here but they could always change with time.

6) To add the roles you will need to right click on My computer and pick Manage. Then you will find the IIS role listed and you can add role services like window’s authentication.

7) Now we are ready to start moving files.
This is the command to run on your old IIS 6 box
msdeploy -verb:sync -source:metakey=lm/w3svc/(site ID) -dest:package=c:\(site ID).zip > WebDeployPackage.log
Remember to change the (site ID) to the correct ID for the webpages. This will make folders that have all the files we need to move. Now I just used a thumb drive and move the files to the new IIS 7 box.

8) Now we run the command
msdeploy -verb:sync -source:package=c:\(Site ID).zip -dest:metakey=lm/w3svc/(Site ID) -whatif > WebDeploySync.log
This will let us know what will happen when we run the real command. The – whatif is what makes it a test run. If everything looks correct (should look like its just moving files) then you will run this line

9) msdeploy -verb:sync -source:package=c:\(Site ID).zip -dest:metakey=lm/w3svc/(Site ID) > WebDeploySync.log
If everything worked correctly you should be able to test your sites now and they will work.


