---
title: Media wiki Manual updating Error
description: 
published: true
date: 2021-04-23T17:40:48.485Z
tags: 
editor: markdown
dateCreated: 2021-04-23T17:40:48.485Z
---

While processing of manual upgrading Mediawikki, some old files can cause problems with the new version.

 
---------------------------------------

PHP Fatal error: Cannot redeclare wfProfileIn() (previously declared in /users3/data/i/insightdigital.org-79155/public_html/team/includes/profiler/Profiler.php:33) in /users3/data/i/insightdigital.org-79155/public_html/team/includes/ProfilerStub.php on line 24

---------------------------------------

 

In order to fix this error, Rename the StartProfiler.php to startProfiler.php.bak

If you are not using profiling, but have a StartProfiler.php file in the MediaWiki root folder, you may receive errors referring to /includes/Profiler.php. Deleting, or renaming, the StartProfiler.php file will resolve this error. The StartProfiler.sample file, also in the MediaWiki root folder, can serve as a template should you enable profiling in the future.

 

======================================

mv StartProfiler.php StartProfiler.php.bak

php maintenance/update.php 

======================================

Reference ticket ID : QQU-929-37677