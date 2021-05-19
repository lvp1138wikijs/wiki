---
title: RDP: Invalid License Issue
description: 
published: true
date: 2021-05-19T06:08:01.891Z
tags: 
editor: markdown
dateCreated: 2021-05-19T06:08:01.891Z
---

Problem: Following Error message is appearing when log in to server via remote desktop  

> RDP Session Error
> 
> "The remote session was disconnected because there are no remote desktop license servers available to provide a license"
{.is-danger}

**Solution**:

Disable RDP licencing mode.

You can login server by using the following steps

- Go to start >> Run
- Type command : mstsc /v:xxx.xxx.xxx.xxx /admin and then hit enter.  (replace xxx.xxxx with server IP address)

Then Uninstall RDP license role

- Open Server Manager. To open Server Manager, click Start, point to Administrative Tools, and then click Server Manager.
- In the left pane, expand Roles.
- Right-click Remote Desktop Services, and then click Remove Role Services.
- On the Select Role Services page, clear the Remote Desktop Licensing check box, and then click Next.
- On the Confirm Removal Selections page, click Remove.
- On the Removal Progress page, removal progress is noted.
- On the Removal Results page, you are prompted to restart the server to finish the removal process. Click Close, and then click Yes to restart the server.
- If you are prompted that other programs are still running, do either of the following:
  - To close the programs manually and restart the server later, click Cancel.
  - To automatically close the programs and restart the server, click Restart now.
- After the server restarts and you log on to the computer with the same user account, the remaining steps of the removal process finish automatically. When the Removal Results page appears, confirm that the removal of RD Licensing succeeded, and then click Close.

Reference: http://technet.microsoft.com/en-us/library/cc755232.aspx
