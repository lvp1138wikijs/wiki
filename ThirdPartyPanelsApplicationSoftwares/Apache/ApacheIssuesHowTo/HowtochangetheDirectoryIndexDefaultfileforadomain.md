---
title: How to change the DirectoryIndex( Default file) for a domain
description: 
published: true
date: 2021-06-16T17:45:31.486Z
tags: 
editor: markdown
dateCreated: 2021-06-16T17:45:31.486Z
---

To change the default file for the domain we will need to override the Directory Index set in the apache conf.

For a single domain you can follow the steps given below to do that.

1) Edit the .htaccess file in the DocumentRoot for the domain

```
cd /home/username/public_html

vi .htaccess
```

Note : Replace username with the actual username. Assuming the documentroot for the domain is /home/username/public_html

2) Add the following line to the .htaccess file

```
DirectoryIndex index.php index.htm index.html
```

This will make the default file as index.php.  If index.php is missing it will be searching for index.htm and then index.html. 

3) Now save and exit the .htaccess file