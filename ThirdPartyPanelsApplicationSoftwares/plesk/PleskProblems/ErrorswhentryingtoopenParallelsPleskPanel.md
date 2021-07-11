---
title: Errors when trying to open Parallels Plesk Panel
description: 
published: true
date: 2021-07-11T00:54:37.081Z
tags: 
editor: markdown
dateCreated: 2021-07-11T00:54:37.081Z
---

When trying to access Parallels Plesk Panel, browser displays one of the following errors:

```
ERROR: SWKeyExFatalError
xmlrpc error: XML parsing failed

0: common_func.php3:4523
of_get_key_by_product(string 'plesk-win')
1: common_func.php3:4523
getPleskKey()
2: common_func.php3:4602
getKeyProp(string 'demo')
3: auth.php3:54
```

```
Fatal error: Call to undefined function of_get_key_by_product() in C:\plesk\admin\plib\common_func.php3 on line 4501
```

```
It is also not possible to retrieve the key number with the utility keymng.exe, due to an unexpected error:
>"%plesk_bin%\keymng.exe" --get-key-number
Unexpected error
```

The above error indicates that **registry.xml** file may have gone corrupted.

Check the size of the file **%plesk_dir%\admin\repository\registry.xml**. If the file is empty and equals 0KB, delete this file.
Once it is deleted, try to access Parallels Plesk Panel again. A new file should have been generated automatically.