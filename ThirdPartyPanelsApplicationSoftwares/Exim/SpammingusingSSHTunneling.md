---
title: Spamming using SSH Tunneling
description: 
published: true
date: 2022-01-23T06:13:24.114Z
tags: 
editor: markdown
dateCreated: 2022-01-23T06:13:24.114Z
---

# Spamming using SSH Tunneling

We have seen different methods of spamming like spamming using a compromised email account, spamming using a php script etc. All this type of spamming techniques leaves some logs or evidence in the server which can be used to track down the origin of the spam mails. Here we discuss about a different type of spamming that can be done using ssh tunneling or ssh port forwarding.

An attacker can use ssh tunneling to send out spam mails from your server. This type of attack can be difficult to detect as it leaves only little log evidences.

**This type of spamming method need access to a user account in the server**.
Suppose if a user uses a weak password and it gets compromised by the attacker.

Port forwarding via SSH (SSH tunneling) creates a secure connection between a local computer and a remote machine through which services can be relayed. 

**This type of attack even works if the user has /bin/false or /sbin/nologin shell**, provided a password has been assigned to this user. As ssh tunneling do not need a valid shell to work.
Following is what happens at the end of attacker:

ssh -fN -L 3500:localhost:25 testuser@test.com
Here testuser is the compromised account in our server and test.com is the hostname of our server.

What happens here is that the above command forwards the local port 3500 of the attacker to the remote port 25 of the server.
Attacker can now connect to the smtp port of the server via his local port 3500.

How can we prevent this type of attack:

The simplest way to prevent this type of attack is by disabling TCP port forwarding in your sshd configuration file.
In /etc/ssh/sshd_config
##########################
AllowAgentForwarding no
AllowTcpForwarding no
X11Forwarding no
#########################

**This will not deny the actual ssh connection to be established; it will only deny the ability to exploit the forwarding.**

So if we now try to do ssh tunneling we will get the following error:


channel 2: open failed: administratively prohibited: open failed

> NB: Also make sure to use a strong and complex password for all the users.
{.is-info}
