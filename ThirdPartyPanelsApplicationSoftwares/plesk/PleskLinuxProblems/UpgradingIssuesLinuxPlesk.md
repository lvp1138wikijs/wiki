---
title: Upgrading Issues - Linux Plesk
description: 
published: true
date: 2021-07-11T00:34:17.090Z
tags: 
editor: markdown
dateCreated: 2021-07-11T00:34:17.090Z
---

# Upgrading Issues - Linux Plesk

**Plesk ERROR: Zend_Log_Exception**

Issue: After Parallels Plesk Panel upgrade to version 10.0.1 the following error message is shown on the login page:

```
ERROR: Zend_Log_Exception
"/usr/local/psa/admin/logs/panel.log" cannot be opened with mode "a"

0: Stream.php:66
        Zend_Log_Writer_Stream->__construct(string '/usr/local/psa/admin/logs/panel.log')
1: Abstract.php:84
        CommonPanel_Application_Abstract->_initLog()
2: Abstract.php:31
        CommonPanel_Application_Abstract->run()
3: Abstract.php:19
        CommonPanel_Application_Abstract::init()
4: auth.php3:137
```

**SOLUTIONS**

This issue has been discussed in KB Parallels forum. Here is the link :: http://kb.parallels.com/9266

