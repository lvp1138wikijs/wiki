---
title: Disk quota full - unable to login to cPanel.
description: 
published: true
date: 2021-12-27T15:09:24.503Z
tags: 
editor: markdown
dateCreated: 2021-12-27T15:09:24.503Z
---

# Disk quota full - unable to login to cPanel.


Normal symptoms of this case are as given below:

1. Unable to login to cPanel.

2. Unable to login to webmail.

3. Emails associated with the account not working.

4. Email sent to the email account bounces back with error "Mailbox quota exceeded".

In order to resolve the above issues caused by exceeding the disk space, please do the following steps:

- **Identify the files that is using the Disk space**: In order to identify the files that is using the disk space, you may need to increase disk quota temporarily by contacting your hosts.Once you gain access to cPanel browse through to "Disk Space Usage" under the "File" tab. It shows the usage of the folders both in a graphical as well as numeric representation. The graphical representation helps you to get a general idea of the disk usage. Whether its the site files, mails or any other folders that use the excessive disk space. When you scroll down the page you see the more illustrated numeric representation. You can view the disk usage of individual files under your account based on disk space that it uses. Based on these details you can decide if the files are needed or not. If any unwanted old files are found you can remove it from the account hence freeing up space.


**Files you can check**.

1. **Old site files**:You can always use the backup option to take a backup of the account before deleting the unwanted files. You can re-upload from backup just in case you need it in future.

1. **Mail folders containing old emails**: In case you do want keep the old emails and are not willing to upgrade the disk quota, you can always download the emails to your local PC or phone by using an email client.

1. **Email trash folder**: In many cases the deleted emails are moved to the trash folder. You can use the Disk space usage feature to check this. Once you confirm, then emptying the trash folder can be done by using cPanel File Manager.

1. **tmp folder using up space**: tmp folder is used to store the logs files of various analytic cPanel logs such as that of analog, awstats, webalizer etc.. you can delete these so as to free up disk space.


