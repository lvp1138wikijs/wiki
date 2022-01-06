---
title: Install Zend Framework under Linux Cpanel shared account
description: 
published: true
date: 2022-01-06T04:57:36.294Z
tags: 
editor: markdown
dateCreated: 2022-01-06T04:57:36.294Z
---

# Install Zend Framework under Linux Cpanel shared account

1. **Download Zend Framework.**

- Note: Adobe FlashBuilder will install a local copy of Zend on your computer’s local server (if you have one). You can just use that install of Zend Framework instead of downloading a new one.
- Get Zend Framework from zend.com and extract the contents to your local disk. The free version should be sufficient for FlashBuilder.
- Extract ZendFramework-XX.tar.gz and rename ‘ZendFramework-x.x.x’ folder to /ZendFramework.

2. **Upload your local /ZendFramework folder to cPanel**.

- Note: There is some indication from Adobe that the Zend Framework needs to be within your website. I have always known that for security and privacy reasons, the bulk of your PHP code should never be stored on your website. It should be stored in some directory outside of (below) your website directory. For example, where your website might be /home/cPanelUsername/public_html/, PHP should be stored in/home/cPanelUsername/php/. (You may have to change the read/write/etc. permissions to this directory in order to have you website access PHP. That is beyond the scope of this tutorial, though.)
- Make sure FTP transfers the files in binary mode (BIN).
- Copy down the name of your sites’ Zend Framework directory. E.g.,/home/cPanelUsername/php/ZendFramework

3. Display and record your PHP directory information.

- Create a file ‘info.php’ with the following line in it:
```
<?php phpinfo(); ?>
```
- Visit your site in your browser, and go to http://yourWebsite/info.php.
- Make a note of the DOCUMENT_ROOT value.
- Make a note of the include_path value.
- It is a good idea to delete this file now; you don’t want others seeing your PHP setup.

4. **Create a local php.ini file for your Flex pages**.

- Create php.ini file in the site folder where you are going to be running Flex. E.g., public_html/FlexTests/php.ini.
- Add your Zend Framework library path in the include path variable include_path, and turn onallow_url_fopen, and allow_url_include in this php.ini file: , allow_url_fopen and allow_url_include functions. E.g.:

```
include_path = "{the include_path settings you recorded above}:{the path to your Zend Framework directory. E.g., the DOCUMENT_ROOT setting recorded above}/ZendFramework/library"
allow_url_fopen = On
allow_url_include = On
```

5. Tell Apache that it is ok to use your php.ini file.

- If there is no .htaccess file in your site’s Flex directory, create a new text file called .htaccess. If there is one there already, open that .htaccess file.
- Within the .htaccess file, add this line.

```
SetEnv PHPRC /home/cpusername/public_html/php.ini
```

- Note that /home/cpusername/public_html should be to the actual directory for your php.ini file.  That way, you can conveniently store your php.ini file.
- Also note that the .htaccess file should be located in the same directory as – or a parent directory of – your Flex file(s).  Please research Apache’s .htaccess for more information

6. **Test the Zend install**.

- In your site’s Flex directory, create a testZend.php file. Add the following code:

```
<?php
require_once 'Zend/Version.php';
echo 'Zend Framework version ' . Zend_Version::VERSION;
//require_once 'Zend/Mail.php';
//$mail=new Zend_Mail();
echo ' - it is working';
?>
```
- Go to your website using the browser, and access your Flex directory:http://www.yourdomain.com/FlexTest/testZend.php
- It will show “It is working” message if everything goes well.
