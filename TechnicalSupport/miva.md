---
title:  Upgrade Miva Merchant Empresa 
description: 
published: true
date: 2022-01-21T12:48:59.202Z
tags: 
editor: markdown
dateCreated: 2022-01-21T12:48:59.202Z
---

Upgrading Miva Empresa Virtual Machine on UNIX/Linux servers is usually simple. Please follow these steps:

1. Read the release notes for the latest release of Miva Empresa. Check these to see if there are any settings that may effect your installation or server OS. Release notes can be found on the Miva Corporation website at: http://www.miva.com/docs/empresa/

2. Once you have read the release notes, download the Miva Empresa Virtual Machine distribution from the Miva Corporation FTP Site. You should have the FTP information from when you originally purchased the engine from Miva.

If you do not have this information, please contact Miva Technical Support. Include your Miva Empresa Virtual Machine license number. Once validated, we will supply you with the download information.

3. You may FTP using your Local Machine, or right from a TelNet/SSH session on the server. The FTP site will include a separate folder for each different operating system support by Miva. Open the folder that applies to your system. Each folder may contain a different packaging format; download the appropriate file. Save the files in a temporary location on your local machine, or on the server.


4. Expand the package in the temporary directory where it was downloaded. It will create a folder: "mivavm-v5.xx" which, in turn, contain the file(s) necessary for the upgrade.

 In our cases the packages is http://www.miva.com/miva-software/empresa/mivavm-v5.23-linux_x64.tar.gz and after extraction we will get a folder named "mivavm-v5.23"


5. Locate the "cgi-bin" subdirectory. It will contain a file: "mivavm-5.xx " (5.xx = version number). This is the Miva Empresa Virtual Machine binary.

6. Also, in the unpackaged distribution folder, locate the "lib" subdirectory. It will contain a folder: "builtins". This is the Builtins directory that contains libraries for the Miva Empresa Virtual Machine. This folder, and it's contents, will need to be uploaded to the server, along with the "mivavm-v5.xx" file.

7. In the same "lib" subdirectory, you will also see a folder called "config". Inside of this folder are two library files: "3x.so" and "env.so" . Upload both of these libraries to the same temporary folder as the "builtins" files and the "mivavm-v5.xx " file.

8. If the files are not already uploaded to the server, upload them to a temporary directory. Once uploaded on the server, rename the "mivavm-v5.xx" file to just "mivavm ":

mv mivavm-5.xx mivavm

9. Then, copy this file to the location in which it will be run from and where the old Miva Binary is:
o Server-Safe Mode: The Miva Empresa Virtual Machine binary is run from the Global CGI-Bin. Once you have copied the file, reset the permissions and ownerships:

chmod 4755 mivavm
chown root mivavm
o Standard Mode: The Miva Empresa Virtual Machine binary is run from each site's Individual CGI-Bin. Once you have copied the file, reset the permissions and ownerships:

chmod 4755 mivavm
chown USER mivavm (USER = the user that owns most of the files, including Miva Merchant program and data files.)

10. Locate the Builtins directory on your server. It can be in a number of places, so it is best to look for where it is specified in the Miva Empresa Virtual Machine Configuration files.

o If using a Look in this file for six tags that start with . There will be a path in these tags to the location of the Builtins directory.
o If using the SetEnv tags in httpd.conf: Look in this file for the SetEnv MvCONFIG_DIR_BUILTIN tag. This will have the path to the Builtins directory.

11. Once the Builtins directory is located, overwrite the existing directory with the one from the distribution file.

12. Next, you need to determine which of the two configuration libraries, "3x.so" or "env.so", you are using. If you are using a mivavm.conf file for the Miva Empresa Virtual Machine configuration, then you are using the "3x.so".

If you are using the SetEnv tags in the httpd.conf, then you are using the "env.so". Once you've determined which library you are using, rename it to libmivaconfig.so and place it in the cgi-bin. This should overwrite the existing one.

13. This will usually complete the upgrade process, we can view if the upgrade is completed or not using the diagnostic url  like "http://www.shoppersrule.com/diagtool.mvc ". Make sure the "diagtool.mvc" file is present in the document root, if its not available copy it from the downloaded package. 