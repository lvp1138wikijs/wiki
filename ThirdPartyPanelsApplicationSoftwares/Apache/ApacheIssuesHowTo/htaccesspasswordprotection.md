---
title: .htaccess password protection: Securing a folder in a website
description: 
published: true
date: 2021-06-16T18:17:39.048Z
tags: 
editor: markdown
dateCreated: 2021-06-16T18:17:39.048Z
---

If you have any sort of sensitive documentation or private web application that you want to secure behind a username and password field, then .htaccess is a simple and easy way to start. This is done through the use of a .htaccess file and a .htpassword file. Either the entire website or a specific folder can be password protected.
 

The .htaccess file is placed within the folder and links to a .htpasswd file that contains the login and password information. Typically the .htpasswd file is stored the same directory as the .htaccess file.


**Making a .htaccess file**

The .htaccess file should be placed inside of the directory that you want to secure. The file should contain the following code. 

```
AuthUserFile /home/username/secrets/.htpasswd
AuthGroupFile /dev/null
AuthName "You Shall Not Pass!!"
AuthType Basic
Require valid-user
```

The first line "AuthUserFile" is the full server path to your htpasswd file. You will need to edit this line so that it references the correct location of the .htpasswd file.

> Please note that this is not a URL, this is a server path, and in a Linux file system, will start with a /. You should also not put your .htpasswd file in a web accessible directory.
{.is-info}

Edit the line that starts with "Require valid-user" so that you enter the username of those who you want to give access to. This applies if you had an htpasswd file that had multiple users setup in it and you wanted each one to have access to an individual directory. If you wanted the entire list of users to have access to that directory, you would replace Require user xxx with require valid-user.

The AuthName is the name of the area you want to access. It could say anything, such as "You Shall Not Pass!!". Feel free to change this to whatever you want.


**Generating a password file**

There are a bunch of different ways to generate a .htaccess files. If you don't have command line access, just google "generate .htpasswd file" and you will be set.

```
USAGE: Command -c PATH UserName
Example : htpasswd -c /home/username/secrets/.htpasswd Obama
```



