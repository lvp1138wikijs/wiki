---
title: VMware Vsphere cannot connect to server
description: 
published: true
date: 2021-12-23T15:35:14.049Z
tags: 
editor: markdown
dateCreated: 2021-12-23T15:35:14.049Z
---

# VMware Vsphere cannot connect to server


Fix for the error:

VSphere Client could not connect to serverIP

An Unknown connection error occurs. (The Client could not send a complete request to the server)

(The underlying connection was closed: An unexpected error occurred on a send.))



You can refer the URL: http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003490

For troubleshooting purposes, it may be necessary to restart the management agents on your ESX host. This article provides steps to restart the management agents (mgmt-vmware and vmware-vpxa) directly on ESXi/ESX.


**Restarting the Management agents on ESXi**

To restart the management agents on ESXi:

**From the Direct Console User Interface (DCUI)**:

1. Connect to the console of your ESXi host.
1. Press F2 to customize the system.
1. Log in as root.
1. Use the Up/Down arrows to navigate to Restart Management Agents.

Note: In ESXi 4.1 and ESXi 5.0, 5.1 and 5.5, this option is available under Troubleshooting Options.

5. Press Enter.
6. Press F11 to restart the services.
7. When the service has been restarted, press Enter.
8. Press Esc to log out of the system.

**From the Local Console or SSH**:


1. Log in to SSH or Local console as root.
1. Run these commands:

```
/etc/init.d/hostd restart
/etc/init.d/vpxa restart
```

Note: In ESXi 4.x, run this command to restart the vpxa agent:

```
service vmware-vpxa restart
```

Alternatively:

- To reset the management network on a specific VMkernel interface, by default vmk0, run the command:

```
esxcli network ip interface set -e false -i vmk0; esxcli network ip interface set -e true -i vmk0
```

Note: Using a semicolon (;) between the two commands ensures the VMkernel interface is disabled and then re-enabled in succession. If the management interface is not running on vmk0, change the above command according to the VMkernel interface used.

- To restart all management agents on the host, run the command:

```
services.sh restart
```

**Restarting the Management agents on ESX**

To restart the management agents on an ESX host:

- Log in to your ESX host as root from either an SSH session or directly from the console.
- Run this command:

- service mgmt-vmware restart

- **Caution**: Ensure Automatic Startup/Shutdown of virtual machines is disabled before running this command or you risk rebooting the virtual machines. For more information, see Restarting hostd (mgmt-vmware) on ESX hosts restarts hosted virtual machines where virtual machine Startup/Shutdown is enabled (1003312) and Determining whether virtual machines are configured to autostart (1000163).

- Press **Enter**.
- Run this command:

- service vmware-vpxa restart

- Press **Enter**.
- Type logout and press Enter to disconnect from the ESX host.

- If this process is successful, it appears as:

```
[root@server]# service mgmt-vmware restart
Stopping VMware ESX Server Management services:
VMware ESX Server Host Agent Watchdog [ OK ]
VMware ESX Server Host Agent [ OK ]
Starting VMware ESX Server Management services:
VMware ESX Server Host Agent (background) [ OK ]
Availability report startup (background) [ OK ]
[root@server]# service vmware-vpxa restart
Stopping vmware-vpxa: [ OK ]
Starting vmware-vpxa: [ OK ]
[root@server]#
```

