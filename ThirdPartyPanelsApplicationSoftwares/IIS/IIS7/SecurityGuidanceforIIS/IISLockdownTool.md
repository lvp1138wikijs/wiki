---
title: IIS Lockdown Tool
description: 
published: true
date: 2021-12-20T20:08:25.254Z
tags: 
editor: markdown
dateCreated: 2021-12-20T20:08:25.254Z
---

> Applies To: Windows 7, Windows Server 2008, Windows Server 2008 R2, Windows Vista
{.is-info}


The IIS Lockdown Tool functions by turning off unnecessary features. This reduces the attack surface available to an attacker. To provide in-depth defense or multiple layers of protection against an attacker, URLscan, with customized templates for each supported server role, has been integrated into the IIS Lockdown Tool.

However, to help keep your server secure and to stay protected against known security vulnerabilities, you must install all critical updates.

All the default security-related configuration settings in IIS versions 6.0 and 7.0 meet or exceed the security configuration settings made by the IIS Lockdown tool. Therefore, you do not have to run this tool on Web servers that are running IIS version 6.0 or 7.0. However, if you are upgrading from an earlier version of IIS, you should run the IIS Lockdown Tool before the upgrade to enhance the security of your Web server.

Microsoft has released an updated version of Internet Information Services (IIS) Lockdown Tool 2.1, which provides templates for the major IIS-dependent Microsoft products.

Here is a list of the new features in IIS Lockdown Tool 2.1:

- **Server roles**. Version 2.1 is driven by supplied templates for the major IIS-dependent Microsoft products. These include Microsoft Exchange Server 5.5 and Exchange 2000 Server, Microsoft Commerce Server, Microsoft BizTalk Server, Microsoft Small Business Server 4.5 and 2000, Microsoft SharePoint Portal Server, Microsoft FrontPage Server Extensions, and SharePoint Team Services.
- **URLscan integration**, with customized templates for each supported server role. This integration enables the IIS Lockdown Tool to provide additional security enforced by URLscan without requiring the administrator to design a custom URLscan filter for the particular server configuration and application.
- **Ability to remove or disable IIS services**. Services such as HTTP, FTP, SMTP, and NNTP can be removed or disabled.
- Support for scripted or unattended installation. The tool can read from an answer file.
- **Redesigned user interface and fixes**. In response to user feedback, the IIS Lockdown Tool offers an improved user experience.


> You can download the IIS Lockdown Tool from the Microsoft Website.
> 
> http://support.microsoft.com/kb/325864
{.is-info}


