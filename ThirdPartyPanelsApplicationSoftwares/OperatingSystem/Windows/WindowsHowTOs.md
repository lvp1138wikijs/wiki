---
title: Windows How TOs
description: 
published: true
date: 2021-05-15T05:32:07.160Z
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


## How to Create a script set that will query windows systems for last windows update date and time

You use it by putting a list of the servers you want to check in the servers.txt file, running the Get_results script, and then viewing the results in the results text file. All times are UTC.

It consists of four parts:

1. servers.txt is where a list may be entered of servers names or ips to check updates on.
2. LastUpdateScript.vbs is the query that gathers the last Windows update time from the registry of servers specified in servers.txt
3. Get_results.cmd is the script that runs the query and generates the results to a text file
4. results.txt is the resultant list of servers and last update times
a. This is a text file that may be imported cleanly into Excel by using space as the delimiter.

Joseph

_______________________________________________

servers.txt example: (just a simple text file with a vertical list
_______________________________________________

SERVER1
SERVER2
SERVER3
DB1
DB2

(you get the picture)

_______________________________________________

LastUpdateScript.vbs
_______________________________________________

'Script pulls last Windows update info from registry of all computers specified in computers text file and echos on screen

On Error Resume Next

Set objGetComputerList = CreateObject("Scripting.FileSystemObject")
Set fsoReadComputerList = objGetComputerList.OpenTextFile("servers.txt", 1, TristateFalse)
aryServers = Split(fsoReadComputerList.ReadAll, vbCrLf)
fsoReadComputerList.Close

For Each strComputer In aryServers

Const HKEY_LOCAL_COMPUTER = &H80000002

strKeyPath = "SOFTWARE\Microsoft\Windows\CurrentVersion\WindowsUpdate\Auto Update\Results\Detect"
strEntryName = "LastSuccessTime"
Set objReg=GetObject("winmgmts:{impersonationLevel=impersonate}!\\" & _
strComputer & "\root\default:StdRegProv")
objReg.GetStringValue HKEY_LOCAL_COMPUTER, strKeyPath, strEntryName, strValue
Wscript.Echo(strComputer & " " & strValue)

Next

_______________________________________________

Get_Results.cmd
_______________________________________________

Echo Off
CScript.exe //NoLogo "E:\Tools\Scripts\Last Windows Update Tool\LastUpdateScript.vbs" > "E:\Tools\Scripts\Last Windows Update Tool\results.txt"
setLocal EnableDelayedExpansion

results.txt (sample output)

SERVER1 2012-05-30 02:43:47
SERVER2 2012-05-30 02:43:47
SERVER3 2012-05-30 02:47:14
DB1 2012-05-30 02:46:11
DB2 2012-05-30 02:43:47


## How to Kill a terminal session on a server

- Open a command prompt ( win key + R) type cmd and hit enter.
- Type in "qwinsta /server:<YourServerName>"
- This will let you view all open sessions.
 
- Select the session you would like to kill and type in "rwinsta /server:<YourServerName> <SessionId>"
- This will kill the listed session.

- Now you will be able to remote in.
  
## Add a zone (domain name) to DNS in Windows 2008
  
1. Open DNS management under administrative tools. Start Menu - Control Panel - Administrative Tools – DNS. 

2. Expand forward lookup zones by clicking on the +.

3. Right click on forward lookup zones and click on new zone. You can click on action – new zone.(Or from the Action menu click on new zone.) 

4. Click next and choose primary zone. 

5. Type in the domain name as the zone name without the www. For example type in example.com which is a FQDN (Fully Qualified Domain Name). Then click next. 

6. Leave the option to create a new file selected and click on next. 

7. Leave the last bubble checked as “Do not allow dynamic updates” and click on next. 

8. Now click on finish.
  
## Add a user to Windows Server 2008
  
1. Login to your server through Remote Desktop. Instructions can be found here.

2. Open Server Management by navigating to Start Menu --> Control Panel --> Administrative Tools --> Server Manager. 

3. Expand Configuration and then Users and Groups. 

4. Right click on Users and select new user. Fill in the form. 
    User Name: The user name the user will login with. 
    Full Name: User's full name. 
    Description: Usually the user's role on the server. 
    Password: Password for the user, make sure to make the password at least 8 characters long and it  must include a special character, multiple case, and a number. 
    Click create to add the user.
  
  
## Add records to DNS in Windows 2008
  
A domain name needs zone records to resolve to the correct IP address and server. These records are created in DNS in Windows 2008 on your dedicated server. Follow the directions below to setup these records.

**A record (www / subdomains)**

1. Open DNS management under administrative tools. Start Menu - Control Panel - Administrative Tools – DNS. 

2. Expand forward lookup zones by clicking on the +. 

3. Right click on the zone (domain name) and click on new host (A or AAAA). 

4. Type in the name of the record. If you are creating www then type in www, if you are created a sub domain such as dev.example.com or test.example.com then type in the sub domain name. 

5. Type in the IP address of the domain name or the sub domain. This is usually the primary IP address of your dedicated server. 

6. After typing in the IP address click on add host. 

Congratulations you have added an A record to your domain name.

You will also use A records to add the mail record to your domain name. Follow the instructions above but name the record “mail” and point it to your dedicated server’s email IP address.

**CName Record (www / subdomains)**

A cname record is a canonical record or alias of a domain name. This is the best method for adding the www record or sub domains to your FQDN (Fully Qualified Domain Name).

1. Open DNS management under administrative tools. Start Menu - Control Panel - Administrative Tools – DNS. 

2. Expand forward lookup zones by clicking on the +. 

3. Right click on the zone (domain name) and click on new alias (cname). 

4. Type in the alias name for example www or the sub domain name. 

5. Type in the Fully Qualified Domain Name (FQDN) that the alias will resolve to. If you are setting up www then simply type in your domain name without the www.

**MX Record (email)**

MX records are used to tell mail servers where to send email.

1. Open DNS management under administrative tools. Start Menu - Control Panel - Administrative Tools – DNS. Expand forward lookup zones by clicking on the +. 

2. Right click on the zone (domain name) and click on new mail exchanger (MX). 

3. Leave the host or child domain blank. Under Fully Qualified Domain Name (FQDN) type in the mail server address. For example mail.your-domain-name.com. The mail server priority is for multiple MX records and servers. Dedicated servers only have one mail server so you can leave this at 10  
  
## Block IP address with Windows Firewall 2008

 1. Log into your server via RDP.

2. Click on start > administrative tools > windows firewall with advanced security. 

3. On the left side of the firewall window click on the inbound rules option.

4. On the right side of the screen click on New Rule.

5. Click on the custom radio button and then click next.

6. Make sure the All programs radio is selected then click next.

7. On the protocol and ports options leave everything at its defaults and click next.

8. On the scope screen you will see two boxes the top one is for local IP addresses and the bottom is for remote IP addresses. In this scenario we are trying to block an outside (remote) IP from accessing anything on the server so we will need to add the IP address to this section only as it will not be a local IP address. 

9. Click on the radio that says "these IP addresses " in the remote section

10. Click on the Add button

11. In the next window we will be adding a single IP address to the rule, you can also add an entire range at this point if you wish.

12. Click ok, click next.

13. Make sure you select the Block the connection radio on the next screen and then click next. 

14. Leave all of the options on the next screen checked this will be sure to block the IP no matter the connection they are trying to use. Click next.

15. Name the rule on the next screen something you can remember in case you wish to remove or edit it in the future. Click finish and thats it
  
## Configure Custom Name Servers
  
1. You will need to choose which domain name you want to use as your name server. You are going to be creating ns1.your-domain-name.com and ns2.your-domain-name.com so choose the domain name you are ok with publicly displaying as a DNS server. For example abc.com uses ns1.abc.com and ns2.abc.com. But we also could have chosen ns1.abc.net. 

2. After you have decided on the domain name you will need to add two A records. Your secondary and primary IP address can be found in your welcome email. If you cannot find them please contact support and we can get them for you. Another clue is to look at the first and second IP address on your network card. 


- Add an A record called NS1 to your domain name in DNS and point it to the primary IP address of your server.
- Add another A record called NS2 and point this to your secondary IP address. 
3. Now that the records have been created you will need to use them for your registered domain name. Name servers for a domain are always changed with the domain name registrar. If you do not remember or know the registrar you can do a WHOIS lookup using the URL below. 

http://who.is/

Once you know who the registrar is you will need to register custom name servers. Each registrar is going to be a little different so you will need to use their help guides or contact their support to learn how.
  
  
## How to find a website using high CPU
  
1. To open task manager, right click on your task bar and choose Start Task Manager

2. The task manager window will open and you will see a list of processes running. If not, click on the processes tab. Filter the list by image name and look for w3wp.exe. W3wp.exe is the process used by IIS to run the site, but you actually need the process identifier.

3. In the task manager window click on View and then click on Select Columns. Choose PID (Process Identifier) and click ok.

4. Now a column will appear next to the image name with the PID number. Find the wswp.exe process with the most CPU usage, watch the CPU column. Note this number, you will need it in the next steps

5. Open command prompt and type the following without the quotes and hit enter: "net start WAS" This starts the Windows Process Activation service which is needed for the next step. 

6. In the same command prompt type the following without quotes and hit enter: "%windir%/system32/inetsrv/appcmd list wp". You should get a response like the one below. 

C:\>%windir%/system32/inetsrv/appcmd list wp
WP "1596" (applicationPool:Applicure Test)

7. Note the number in the quotes, this should be your PID. Then in parentheses is the name of the Application Pool in IIS. Now just open IIS and take a look at your application pools for the one that corresponds to the site with high CPU usage. All of your application pools should have the same name as the websites in IIS, unless you named them differently.
  
## Editing File Permission on your windows server
  
1. Log into Server with administrator using RDP.

2. navigate to the folder or file you wish to edit the permission for through the my computer option within the start menu.

3. Right click on the folder or file and click properties.

4. Select the tab at the top labeled Security and click the Edit button (2008) or if you are on 2003 you will see the add and remove buttons.

5. On this screen you can add and remove user permissions to the folder that you have selected.

6. You can add a user by clicking add and then clicking the locations button, selecting your server, click ok, and then typing the name of the user you wish to add. (if you click check names first it will verify that there is a user by that name already added to the server so this is always recommended).

7. You can remove a user by simply highlighting the user within the upper pane and then clicking remove. 

8. Permissions can be fairly complicated however there are some more basic details listed below for your convenience. You may also want to check out this article here for a more in depth understanding of just how deep windows permissions can go.

Full Control -Permission to read, write, change and delete files and sub-folders. 
Modify -                     Permission to read and write to files in the folder, and to delete current folder. 
List Folder Contents     Permission to obtain listing of files and folders and to execute files. 
Read and Execute -     Permission to list files and folders and to execute files. 
Write -                       Permission to create new files and folders within selected folder. 
Read -                       Permission to list files and folders. 

9. The last thing you will want to notice is whether or not you wish for the permissions you are apply will filter down (for folder permissions only) to everything that is contained within it. Windows will do this automatically however if you click the advanced button on the security tab and then click edit (2008). In windows 2003 you will simply click advanced.

10. Once you are on the advanced security Settings window you will see two boxes on the bottom left. You can select them or deselect them as you see fit.
  
## How To Give write access to files for IUSR
  
1. Right click on the directory that you which to apply anonymous access to or write access and select properties.

2. Click on the security tab.

3. Click Edit and then click Add

4. Within the "enter the object names to select" field type in the name of your server\IUSR and then click the check names button (servername\IUSR)

5. This will bring you back to the security addition tab that was previously opened. Here you will need to add the modify permission by placing a check in the modify box below the allow field. (do not remove the other three that are there by default, Read, LFC,RE)

Read: Allows files or folders to be opened as read-only and to be copied.
 
Write: Allows the creation of files and folders; allows data to be added to or removed from files.
 
List Folder Contents: As per Read but also allows navigation of sub-folders.
 
Read and Execute: As per Read but also allows users to run executable files.
 
Modify: All the above as well as the permission to delete the file or folder.
 
Full Control: Full Control -- including the ability to change ACLs.

7. Once you have done this click apply and then click ok.

8. Click ok again and you are done!
  
  
## How to password protect a directory on your dedicated server
  
1. Log into your dedicated server via RDP.

2. Make sure the directory that you want to password protect is below the directory your domain is pointed at. 
(ex \www\domain.com\newdirectory)

3. Right click on the directory that you wish to password protect and click on properties.

4. Click on the security tab

5. Click on the advanced button and then click change permissions.

6. Make sure both boxes on this are unchecked or your permissions will not work correctly. Click apply and then click add when it asks you if you want to remove all inherited permissions. We do not want to remove all of them. Click ok on the next screen.

7. From here you will need to remove any users that either have IIS in them or IUSR. Make sure that you still have the administrators allowed as well as the users you wish to have access to it (example). Give them all but full access as in the example below.

 

8. Click apply.

9. Once permissions have been applied to the directory, open up IIS Manager. This can be found in the start menu under the 'Administrative Tools' section.

10. In IIS Manager, expand the list of sites and click on the site which points to the directory you want to password protect. Click on the + sign next to the IIS entry for the site to see a list of directories. Navigate to the directory you wish to password protect and highlight that directory.

11. In the list of option on the main middle panel, choose 'Authentication' from the list of options under the 'IIS' heading. It should be the second icon in the list. There are 2 permissions settings that need to be changed. You can enable or disable them from the menu on the far right.

- Anonymous Authentication - Disabled
- Windows Authentication - Enabled
- All other authentication methods listed should be 'Disabled' as well.
12. Close IIS manager and test the site. It should ask for a username and password when attempting to access the directory.  


  
 
