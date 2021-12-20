---
title: Configuring MIME Types in IIS 7
description: 
published: true
date: 2021-12-20T17:58:28.074Z
tags: 
editor: markdown
dateCreated: 2021-12-20T17:58:28.074Z
---

# Configuring MIME Types in IIS 7

> Applies To: Windows 7, Windows Server 2008, Windows Server 2008 R2, Windows Vista
{.is-info}


Multipurpose Internet Mail Extensions (MIME) types identify the types of content that can be served to a browser or a mail client from a Web server. When a browser requests content from a Web server, the browser also requests the MIME type of that content. IIS returns this MIME type as the Content_Type field in an HTTP header before returning the content, so that the browser knows how to process or display that content.

IIS uses a default list of global MIME types to determine which types of content to serve. If a client requests a MIME type that is not defined on the Web server, IIS returns a 404.3 error.

You should enable only those MIME types that are required for the types of content stored on your Web server. This best practice helps reduce the server's attack surface.

> IIS does not allow duplicate MIME types.
{.is-info}

https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc755178(v=ws.10)?redirectedfrom=MSDN


## Add a MIME Type (IIS 7)

You should create MIME types to help clients handle new file name extensions appropriately. If IIS 7 does not recognize the file name extension requested by the client, IIS 7 sends the content as the default MIME type, which is Application. This MIME type signifies that the file contains application data, and usually means that clients cannot process the file.

> Adding a configuration setting adds the setting at the local level and to any child levels that inherit the setting.
{.is-warning}

##  Edit a MIME Type (IIS 7)

You can edit a MIME type to change either the file name extension or the MIME type itself. If you make a change at the Web server level, it applies to all sites, applications, and virtual directories on the server.

> Editing a configuration setting changes the setting at the local level and for any child levels that inherit the setting.
{.is-warning}

**To edit a MIME type**

You can perform this procedure by using the user interface (UI), by running Appcmd.exe commands in a command-line window, by editing configuration files directly, or by writing WMI scripts.

**User Interface**


**To use the UI**

1. Open IIS Manager and navigate to the level you want to manage.
1. In Features View, double-click MIME Types.
1. On the MIME Types page, select the MIME type you want to change.
1. In the Actions pane, click Edit.
1. In the Edit MIME Type dialog box, change the value in the MIME type text box, and then click OK.

**Command Line**

To change a MIME type, use the following syntax:

```
appcmd set config /section:staticContent /[fileExtension='string',mimeType='string'].mimeType:string
```

The variable fileExtension string is a file name extension. The variable mimeType string is a MIME type. For example, to change the MIME type for the .xyz file name extension, type the following at the command prompt, and then press ENTER:

```
appcmd set config /section:staticContent /[fileExtension='.xyz',mimeType='application/octet-stream'].mimetype:text/plain
```

For more information about Appcmd.exe, see Appcmd.exe (IIS 7).

**Configuration**

The procedure in this topic affects the following configuration elements:

<mimeMap> under <staticContent>
  
**WMI**  
  
Use the following WMI classes, methods, or properties to perform this procedure:

    StaticContentSection.MimeMap property

    MimeMapElement class
  
## Remove a MIME Type (IIS 7)
  
 You can remove MIME types to restrict the types of content IIS 7 serves to clients. For example, if you do not want executable files (.exe) to be served, you can remove that MIME type from the global list on the Web server, or at a lower level in the configuration hierarchy if the configuration is not locked at the global level.
  
> Removing a configuration setting removes the setting at the local level and from any child levels that inherit the setting.
{.is-warning}


**To remove a MIME type**
  
You can perform this procedure by using the user interface (UI), by running Appcmd.exe commands in a command-line window, by editing configuration files directly, or by writing WMI scripts.
  
**User Interface**
 
  **To use the UI**

  
1. Open IIS Manager and navigate to the level you want to manage.
1. In Features View, double-click MIME Types.
1. On the MIME Types page, select the MIME type you want to remove from the list.
1. In the Actions pane, click Remove.
1. In the MIME Types dialog box, click Yes.
  
**Command Line**
  
To remove a MIME type, use the following syntax:

```
appcmd set config /section:staticContent /-"[fileExtension='string',mimeType='string']"
```
  
The MIME type must exactly match an existing MIME type. For example, to remove the MIME type for the .xyz file name extension, type the following at the command prompt, and then press ENTER:
  
```
appcmd set config /section:staticContent /-"[fileExtension='.xyz',mimeType='application/octet-stream']"
```
  
**Configuration**  
  
The procedure in this topic affects the following configuration elements:

<mimeMap> under <staticContent>
  
**WMI**  
  
Use the following WMI classes, methods, or properties to perform this procedure:

    StaticContentSection.Remove method  
  
>  To delete an instance of this object, use the object’s Delete_ system method that it inherits from WMI.
{.is-warning}

  