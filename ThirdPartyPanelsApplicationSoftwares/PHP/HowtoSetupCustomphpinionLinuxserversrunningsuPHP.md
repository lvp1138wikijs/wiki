---
title: How to Setup Custom php.ini on Linux servers running suPHP
description: 
published: true
date: 2021-12-21T17:02:07.111Z
tags: 
editor: markdown
dateCreated: 2021-12-21T17:02:07.111Z
---

# How to Setup Custom php.ini on Linux servers running suPHP


suPHP is a tool for executing PHP scripts with the permissions of their owners. If you are setting up custom php settings, the custom php.ini file will be required in a folder where the php script needs to execute. Or you can place php.ini anywhere and have this directive in public_html/.htaccess.

```
suPHP_ConfigPath /home/username/php5-config
```

where username is cpanel account username, and php5-config is just a folder name (name it anything) having php.ini and it will pick php.ini from that folder.

Also keep php.ini out of public_html so that clients don't just try setting php parameters of their own choice.

```
cd /home/username

cp /usr/local/lib/php.ini ./

touch .htaccess

chown username.username php.ini .htaccess
```

Open .htaccess using vi editor and and add "suPHP_ConfigPath /home/username" parameter in /home/username/.htaccess and this php.ini settings will be applied to entire account.