---
title: Cpanel update failure error
description: 
published: true
date: 2021-12-27T15:04:39.276Z
tags: 
editor: markdown
dateCreated: 2021-12-27T15:04:39.276Z
---

# Cpanel update failure error


The customer reports the following error in his mail for the cpanel update, you can try out the following fix.

```
##################################################

[20130711.015501] rpm_is_working ##################################################

[20130711.015501] E Blocker found: Cannot upgrade because Interchange is installed.

[20130711.015501] ***** FATAL: An attempt to up/downgrade to 11.38.1.6 was blocked. Please review blockers.

[20130711.015501] The Administrator will be notified to review this output when this script completes

[20130711.015501] E Detected events which require user notification during updatenow. Will send iContact the log
```

 Try to execute yum update. If yum update is failing because of this please do the following commands:

```
yum remove mod_python
```

The above command will remove the mod_python package.

For updating the RPM packages,please run the below command:

```
yum -y update
```

For updating the Cpanel, please do the following command:

```
/scripts/upcp --force
```

Then recompile apache using the command :

```
/scripts/easyapache --build
```
Reference ticket ID: KJL-579-12824


