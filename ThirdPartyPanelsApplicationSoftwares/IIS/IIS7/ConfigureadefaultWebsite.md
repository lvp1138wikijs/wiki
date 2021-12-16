---
title: Configure a default Web site
description: 
published: true
date: 2021-12-16T19:57:26.656Z
tags: 
editor: markdown
dateCreated: 2021-12-16T19:57:26.656Z
---

# Configure a default Web site


When you install IIS, it is preconfigured to serve as a default Web site; however, you may want to change some of the settings. To change the basic settings for the Web site and to emulate the steps that are required to set up Apache for the first time by using the configuration file:

1. Log on to the Web server computer as an administrator.
1. Click Start, point to Settings, and then click Control Panel.
1. Double-click Administrative Tools, and then double-click Internet Services Manager.
1. Right-click the Web site that you want to configure in the left pane, and then click Properties.
1. Click the Web site tab.
1. Type a description for the Web site in the Description box.
1. Type the Internet Protocol (IP) address to use for the Web site or leave the All (Unassigned) default setting.
1. Modify the Transmission Control Protocol (TCP) port as appropriate.
1. Click the Home Directory tab.
1. To use a folder on the local computer, click A directory on this computer, and then click Browse to locate the folder that you want to use.
1. To use a folder that has been shared from another computer on the network, click A share located on another computer, and then either type the network path or click Browse to select the shared folder.
1. Click Read to grant read access to the folder (required).
1. Click OK to accept the Web site properties.
 
 