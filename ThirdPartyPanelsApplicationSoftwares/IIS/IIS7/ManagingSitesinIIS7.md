---
title: Managing Sites in IIS 7
description: 
published: true
date: 2021-12-20T19:51:47.420Z
tags: 
editor: markdown
dateCreated: 2021-12-20T19:51:47.420Z
---

- [Create a Websites](/ThirdPartyPanelsApplicationSoftwares/IIS/IIS7/AdministrativeTaskwithIIS7)
- 
- View a List of Sites on a Web Server
- Start or Stop a Web site
- Add a Binding to a Site
- Configure a Host Header for a Web Site
- Change an Application Pool for a Site

## View a List of Sites on a Web Server

Open IIS Manager. 

In the Connections pane, click Sites in the tree.

View the list of sites or click a site in the list to modify site properties from the Actions pane.

## Start or Stop a Web site

1. Open IIS Manager and navigate to the level you want to manage.  
1. In Features View, in the Actions pane, use one of the following procedures:

- Under Manage Web Site, click Start to start the Web site.
- Under Manage Web Site, click Stop to stop the Web site.

## Add a Binding to a Site

- Open IIS Manager. 
- 
- In the Connections pane, expand the Sites node in the tree, and then click to select the site for which you want to add a binding.
- 
- In the Actions pane, click Bindings.
- 
- In the Site Bindings dialog box, click Add.
- 
- In the Add Site Binding dialog box, add the binding information and then click OK.


## Configure a Host Header for a Web Site

1. Open IIS Manager. 

1. In the Connections pane, expand the Sites node in the tree, and then select the site for which you want to configure a host header.

1. In the Actions pane, click Bindings.
 
1. In the Site Bindings dialog box, select the binding for which you want to add a host header and then click Edit or click Add to add a new binding with a host header.

1. In the Host name box, type a host header for the site, such as www.serverpoint.com

1. Click OK.

1. To add an additional host header, create a new binding with the same IP address and port, and the new host header. Repeat for each host header that you want to use this IP address and port.

## Change an Application Pool for a Site

1. Open IIS Manager.

1. In the Connections pane, expand the Sites node in the tree, and then click to select a site for which you want to change the application pool.

1. In the Actions pane, click Basic Settings to open the Edit Site dialog box.

1. Click Select to open the Select Application Pool dialog box, and then select an application pool from the Application pool list and click OK.

1. In the Edit Site dialog box, click OK.


