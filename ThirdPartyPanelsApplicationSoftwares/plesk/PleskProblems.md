---
title: Plesk Problems/HowTo
description: 
published: true
date: 2021-07-11T00:49:33.676Z
tags: 
editor: markdown
dateCreated: 2021-07-11T00:49:33.676Z
---

## How to regenerate registry.xml

Registry.xml is a file that contains information about Plesk licenses deployed on a server. When this file becomes corrupted, you may see the following error message in your control panel:


> Error: The license key is invalid. In order to use the Panel, you need to obtain and install a new valid license key.The amount of currently used resources overrides the limits defined by your license. The number of websites hosted on the server exceeds the limits defined by your license. You have X sites hosted; your license allows hosting only X sites. The number of served customer accounts exceeds the limits defined by your license. You have X customer accounts currently served; your license allows serving only X customer accounts.
{.is-danger}

**Resolution**

To fix the registry.xml corruption, simply remove the damaged file. You can find the file in one of the following folders, depending on your OS:

**Linux**:

```
/etc/sw/keys/
```

**Windows**:

```
%plesk_dir%\admin\repository\
```
After the file is removed, log in to Plesk Panel. The registry.xml file will be recreated

Reference: http://kb.parallels.com/en/113381

## How to Recover Admin Password

**Linux**

**For PP versions 10.x**:

Use ${PRODUCT_ROOT_D}/bin/admin utility to prompt the password for user "admin":

```
# /usr/local/psa/bin/admin --show-password
```

Use ${PRODUCT_ROOT_D}/bin/init_conf to reset the password for user "admin":

```
# /usr/local/psa/bin//init_conf -u -passwd <new_password>
```

**For PP versions up to 9.x**:

The PP admin password is stored in a hidden file on the server. Use this command to get it:

```
# cat /etc/psa/.psa.shadow
```

**Windows**

Apart from the password reminder available on the login screen, you can use the plesksrvclient.exe utility located in the %plesk_bin% folder to set up a new password or retrieve the old one.

You can set up a new password by running the following command:

```
"%plesk_bin%\plesksrvclient" -set <new_password> true
```

You can also retrieve the current password by running this utility with:

```
"%plesk_bin%\plesksrvclient" -get
```

To retrieve the password in the command line, you can use -nogui option:

```
"%plesk_bin%\plesksrvclient" -get  -nogui > plesk_password.txt
```

After that, you can find the retrieved Plesk password in the plesk_password.txt file.

Ref: http://kb.parallels.com/346
Ref: http://kb.parallels.com/473

## How to check Plesk Service is UP and running

In window open command prompt and in linux open console and then do a telnet  to port 8443.

```
telnet ipaddress 8443
```
or open you favorite browser and try to open url https://your_ipaddress:8443

## Plesk License Expired Issue

If you are getting a warning message "Plesk Licese Issue has been expired...." and plesk is redirecting to license management window.

Then do the following,

- Check plesk license expire date and license resources.
- If the date is older than the current system date and resource are showing correctly. Then click on Retrieve Keys to retrieve the ordered license key. Plesk License Manager will retrieve the purchased license key from the Plesk licensing server and automatically upload it to your control panel.

If license not upgrading after retrieve keys, then contact Mr. James/ shabi. 






