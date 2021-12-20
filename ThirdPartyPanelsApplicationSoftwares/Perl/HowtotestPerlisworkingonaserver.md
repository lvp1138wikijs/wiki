---
title: How to test Perl is working on a server
description: 
published: true
date: 2021-12-20T20:49:33.431Z
tags: 
editor: markdown
dateCreated: 2021-12-20T20:49:33.431Z
---

# How to test Perl is working on a server

To check if perl is working on a server, please do the following steps:

1.Open a test file using vi editor using the command vi test.pl and enter the following codes:

```
#!/usr/bin/perl
print "Content-Type: text/html\n\n";
print "<html><body><h1>Perl is working!</h1></body></html>";
```

2.Save the file. Then give execute permission to the file :

```
# chmod +x test.pl
```

3.Then browse the file, www.yoursite.com/test.pl (replace yoursite.com with your website name).

