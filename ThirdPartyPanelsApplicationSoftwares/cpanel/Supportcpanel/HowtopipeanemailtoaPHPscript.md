---
title: How to pipe an email to a PHP script
description: 
published: true
date: 2021-12-27T19:57:44.854Z
tags: 
editor: markdown
dateCreated: 2021-12-27T19:57:44.854Z
---

# How to pipe an email to a PHP script


To pipe an email to a PHP script, do the following:

- Login to your Cpanel
- Click on 'E-mail Forwarders'
- Click 'Add Forwarder'
- Fill in the address you wish to be forwarded.
- Select 'Pipe to a Program', then fill in the full path to the php script you will be using.

As for the script itself, here is an example of one that can be used. The script will read the input from the STDIN and save the message in a file named 'mail.txt'. This will be located in the same directory as the script itself.

#!/usr/bin/php –q

There are a few things that should be noted here:

- The first line (called the hashbang) should be the very first thing listed in the script. Any spaces or blank lines will cause bounced error messages.
- The permissions for your script should be set to 755. 
- There should be no closing PHP tag, as this would send the output to the mail server.

```
A test Scripts
--------------
#!/usr/bin/php -q
<?

/* Read the message from STDIN */
$fd = fopen("php://stdin", "r"); 
$email = ""; // This will be the variable holding the data.
while (!feof($fd)) {
$email .= fread($fd, 1024);
}
fclose($fd);
/* Saves the data into a file */
$fdw = fopen("/home/user/public_html/mail.txt", "w+");
fwrite($fdw, $email);
fclose($fdw);
/* Script End */
```

