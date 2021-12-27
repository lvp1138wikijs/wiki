---
title: Internal Server Error on Firewall settings in WHM
description: 
published: true
date: 2021-12-27T15:32:48.926Z
tags: 
editor: markdown
dateCreated: 2021-12-27T15:32:48.926Z
---

# Internal Server Error on Firewall settings in WHM


Getting 500 internal server error while while accessing Firewall settings in WHM, please do the following steps:

```
Internal Server Error
500
No response from subprocess with exit signal: 2
```

1. Check the cPanel error log using the following command:

```
tail -f /usr/local/cpanel/logs/error_log

===============

Can't locate Net/LibIDN.pm in @INC (@INC contains: /usr/local/cpanel /usr/lib/perl5/site_perl/5.8.8/i386-linux-thread-multi /usr/lib/perl5/site_perl/5.8.8 /usr/lib/perl5/site_perl /usr/lib/perl5/vendor_perl/5.8.8/i386-linux-thread-multi /usr/lib/perl5/vendor_perl/5.8.8 /usr/lib/perl5/vendor_perl /usr/lib/perl5/5.8.8/i386-linux-thread-multi /usr/lib/perl5/5.8.8 .) at /usr/local/cpanel/Cpanel/Encoder/Punycode.pm line 10.
Compilation failed in require at /usr/local/cpanel/Cpanel/DomainTools.pm line 13.
BEGIN failed--compilation aborted at /usr/local/cpanel/Cpanel/DomainTools.pm line 13.
Compilation failed in require at /usr/local/cpanel/Cpanel/CheckData.pm line 8.
BEGIN failed--compilation aborted at /usr/local/cpanel/Cpanel/CheckData.pm line 8.
Compilation failed in require at /usr/local/cpanel/Cpanel/cPanelFunctions.pm line 11.
BEGIN failed--compilation aborted at /usr/local/cpanel/Cpanel/cPanelFunctions.pm line 11.
Compilation failed in require at /usr/local/cpanel/whostmgr/docroot/cgi/addon_csf.cgi line 24.
BEGIN failed--compilation aborted at /usr/local/cpanel/whostmgr/docroot/cgi/addon_csf.cgi line 24.
Internal Server Error: "GET /cgi/addon_csf.cgi HTTP/1.1" 500 No response from subprocess with exit signal: 2

===============
```

2. It was a missing Perl module problem. Please install Perl module Net::LibIDN using cpan using the following command:

```
# cpan
cpan> install Net::LibIDN
```

3. you can also install the perl module using the cPanel script.

```
/scripts/perlinstaller --force Net::LibIDN
```



