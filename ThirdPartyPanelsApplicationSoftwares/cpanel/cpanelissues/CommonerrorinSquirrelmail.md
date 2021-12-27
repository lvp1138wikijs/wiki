---
title: Common error in Squirrelmail
description: 
published: true
date: 2021-12-27T14:33:19.916Z
tags: 
editor: markdown
dateCreated: 2021-12-27T14:33:19.916Z
---

# Common error in Squirrelmail


Sometimes you receive the following error while browsing webmail:

```
Warning: main(../config/config.php): failed to open stream: No such file or directory in /usr/local/cpanel/base/3rdparty/squirrelmail/functions/global.php on line 18

Fatal error: main(): Failed opening required ‘../config/config.php’ (include_path=’/usr/local/cpanel/3rdparty/lib/php/:.’) in /usr/local/cpanel/base/3rdparty/squirrelmail/functions/global.php on line 18
```

In order resolve those issues, please run the following command:

```
/scripts/fixwebmail
```

After executing the above command, if you are getting the following error

```
/scripts/fixwebmail
```
Then please execute the following command:

```
cp -p /usr/local/cpanel/base/3rdparty/squirrelmail/config/config_default.php /usr/local/cpanel/base/3rdparty/squirrelmail/config/config.php
```

Refresh the page for squirrelmail , you won’t receive the error.

