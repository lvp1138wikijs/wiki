---
title: Exchange
description: 
published: true
date: 2021-07-24T04:59:38.833Z
tags: 
editor: markdown
dateCreated: 2021-07-24T04:50:24.456Z
---

# Exchange

**How to Setup Exchange Server 2003**

**Pre-Installation Checklist**

Make sure you have all of the following steps in place before you setup Exchange Server 2003.

For simplicity we are assuming you are setting up a small office where one machine will be used for both the Active Directory and the Exchange Server. This setup works just fine and reduces the number of machines to maintain. If you have a larger office you may want to consider separating the Active Directory machine and the Exchange 2003 Server.

1. **You must have IIS (Internet Information Server) installed**.

When you install IIS, you should select the typical install that includes an SMTP component.

2. **Make sure your networking has DNS setup**.

If you use DHCP, the DNS setting should be set, if you do not use DHCP then make sure that you have entered your DNS server names. Exchange Server will use your DNS settings when it sends e-mail to the Internet.

3. **You must have Active Directory setup**. 

To setup active directory, go to Start -> Programs -> Administrative tools -> Configure your server.
Select Active Directory from the left hand panel, then select "Start" in the right hand panel to start the setup wizard.

- Select "Domain controller for a new domain" 
- 
- Take the default - Create a new domain tree 
- 
- Create a new forest of domain trees 
- 
- When it asks for your full DNS name - enter the name of your domain that you have registered. This would be the name to the right of the "@" for your email address, such as "YourCompany.com"
- 
- Accept the Netbios equivalent of your domain in our case "YourCompany"

- Select the locations you want to store the databases
- 
- Accept the location of the system folder
- 
- On the permissions screen select what is appropriate for your network; if all machines are Windows 2003, then select the only Windows 2003 permissions. Otherwise use the default for compatibility.
- 
- Create a password to administer the directory.
- 
- Review your configuration and accept by pressing Next.

After pressing next - the Active Directory configuration wizard will spend several minutes creating the directory for you. When it is complete press finish and reboot the computer.


**Configuring the Exchange Server 2003**

Run the Exchange Server Setup - it will walk you through the following wizard

1. Agree to the licenses agreement 
1. Enter your serial number
1. The next screen will prompt you to select what components you want to install.  The typical configuration is selected. This should be fine with most installation.  If you need you can enable any additional services you wish.
1. At the installation type screen - we are setting up a new organization, so we have used the default selection “Create a new Exchange Organization”.

1. At the organization name screen - enter the name of your company
1. Agree to the license statement
1. Review the your selections and press next to begin

The installation wizard will now install the components you have selected - this will take several minutes to 1/2 hour.  When it is complete you are ready to add your users.

**Adding E-Mail Users**

Go to the start menu -> Programs -> Microsoft Exchange -> Active Directory Users and Computers

On the left hand side of the screen, select users.  Then right click in the right hand panel and select "New" and at the sub menu select "User". You will be presented with a wizard where you enter the users name and e-mail address. Then press next and enter that users password and press next. On the last screen select that you want to create an Exchange Mailbox. When you press finish the user is created and you are ready to enter another user name.


## Exchange 2010 Installation on windows server 2008

 Add the appropriate Windows components/features
        Open PowerShell via the icon on the task bar or Start >> All Programs >> Accessories >> Windows PowerShell >> Windows PowerShell. Be sure that PowerShell opened with an account that has rights to install Windows components/features.
        Run the following command: Import-Module ServerManager
        For a typical install with the Client Access, Hub Transport, and Mailbox roles run the following command:
        
Add-WindowsFeature NET-Framework,RSAT-ADDS,Web-Server,Web-Basic-Auth,Web-Windows-Auth,Web-Metabase,Web-Net-Ext,Web-Lgcy-Mgmt-Console,WAS-Process-Model,RSAT-Web-Server,Web-ISAPI-Ext,Web-Digest-Auth,Web-Dyn-Compression,NET-HTTP-Activation,RPC-Over-HTTP-Proxy -Restart.


For a full matrix of the required Windows components with regards to the Exchange server roles see: http://technet.microsoft.com/en-us/library/bb691354.aspx#WS08R2



If your Exchange server will have the Client Access Server role set the Net.Tcp Port Sharing Service to start automatically

   Open PowerShell via the icon on the task bar or Start >> All Programs >> Accessories >> Windows PowerShell >> Windows PowerShell. Be sure that PowerShell opened with an account that has rights to modify service startup settings.
        Run the following command: Set-Service NetTcpPortSharing -StartupType Automatic


**Exchange 2010 Installation**


Now we're ready to run the Exchange 2010 installer. We'll go through a typical installation that includes the Client Access, Hub Transport, and Mailbox roles. This is what you will want to install if you are only going to be running one Exchange server. If you scale out your Exchange architecture with multiple servers then you will want to familiarize yourself with the Exchange server roles for a proper deployment.


- Logon to the desktop of your soon to be Exchange server with a Domain Admin account.
- Run setup from the Exchange 2010 media.
- Click on "Step 3: Choose Exchange language option" and choose one of the options (Install only languages from the DVD will be fine in most cases).
- Click on "Step 4: Install Microsoft Exchange."
- Click Next at the Introduction page.
- Accept the license terms and click Next.
- Make a selection on the Error Reporting page and click Next.
- Stick with the default "Typical Exchange Server Installation" and click Next.
- Choose a name for your Exchange Organization and click Next.
- Make a selection on the Client Settings page and click Next.
- If you want your Exchange server to be available externally then choose a domain name such as mail.myorganization.com, click Next.
- Make a selection on the Customer Experience Improvement Program page and click Next.
- If all the prerequisites are there then you can click Install.
- Grab a cup of coffee or take a walk while the installation process does its thing.
- When the installation has finished go back to the Exchange installation page click on "Step 5: Get critical updates for Microsoft Exchange."
- Install Microsoft Update (if necessary) so that Windows update will check for non-OS updates, and verify that there are no Exchange updates.


**Post Installation Steps**

Now that you have Exchange 2010 installed, you will need to do some basic configuration in the Exchange Management console to get mail flowing to/from your server.

 Open the Exchange Management Console via Start >> All Programs >> Microsoft Exchange Server 2010 >> Exchange Management Console
 

- Expand Microsoft Exchange On-Premises so you can see: Organization Configuration, Server Configuration, Recipient Configuration, and Toolbox

- Under Organization Configuration >> Hub Transport >> Accepted Domains add a new Accepted Domain for the domain you wish to use for email addresses. For example, your AD domain will be listed by default (i.e. ad.myorganization.com). You will probably want to add "myorganization.com" as an Authoritative Domain.

- Under Organization Configuration >> Hub Transport >> Send Connectors >> New Send Connector ... >> Pick a name such as "MyOrganization Internet Send Connector" >> change the drop down to "Internet" >> Next >> Add ... >> enter "*" in the Address field and check the box to include all subdomains >> OK >> Next. Now, if you want your Exchange server to route mail directly, then click Next on the Network setting page, but if you want to route your email through an upstream provider then select "Route mail through the following smart hosts" and Add ... a mail gateway such as smtp.comcast.net. Click Next >> Next >> Next >> New

- Under Server Configuration >> Hub Transport >> Right-click Default *** >> Properties >> Permission Groups tab, check the box for Anonymous users. This will allow your Exchange server to accept incoming mail delivery from remote mail servers.

- Under Recipient Configuration >> Mailbox, create mailboxes for your existing AD users (or create a new user & mailbox)

- New Mailbox ... >> select User Mailbox >> Next >> Existing users >> Add ... >> select an existing AD account >> OK >> Next >> specify an alias (e.g. the AD user name) >> Next >> New

- If you want to use an SSL certificate for Outlook Web App, IMAP, POP, etc. click on Server Configuration and import or create the certificate.



**Mail Routing Configuration**

Now the final piece you need to configure to receive mail is your external DNS records. The method for configuring your DNS records will depend on whether you host your own DNS or have a provider that hosts it for you. Either way you will need to create an "A" record that points mail.myorganization.com to the IP address of your mail server, and an "MX" record that points myorganization.com to mail.myorganization.com. You will also want to make sure that port 25 is open both inbound and outbound to your Exchange server