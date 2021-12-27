---
title: Related to MySQL
description: 
published: true
date: 2021-12-27T18:53:21.480Z
tags: 
editor: markdown
dateCreated: 2021-12-27T18:53:21.480Z
---

# Related to MySQL


## MySQL disk space issue in cPanel

> Error:
> 
> MySQL quotas showing 0.00MB
> 
> MySQL databases not showing in cPanel
{.is-info}

How to Fix it:

Edit line

**disk_usage_include_sqldbs=1** ( you need to set it to '1' if '0' ) in file /var/cpanel/cpanel.config

And run

#/**scripts/update_db_cache**

## How to correct version?

Edit the following file to correct version:

Replace username with cPanel username

```
/home/username/.cpanel-datastore/_usr_sbin_mysqld_–version 
```

If you have multiple accounts with problem

```
find ./*/.cpanel-datastore/ | grep _usr_sbin_mysqld_–version | awk ‘{system (“rm ” $1)}’ 
```

## Database Created in MySQL but not in cPanel

If client is adding databases in MySQL and it is created successfully but doesn't show up in cPanel

**Fix : Please Reset MySQL password by using WHM** 

## Can not Create MySQL User from cPanel

Newly created Mysql Users do not list in the current users table at the bottom of mysql db user in cpanel

To fix the issue run the following commands

```
/scripts/mysqlup --force

/usr/local/cpanel/bin/updatephpmyadmin --force

/scripts/upcp --force
```

## PhpMyAdmin Login issue


If you are getting following error: #1045 Cannot log in to the MySQL server when trying to access PHPmyadmin via cPanel, then do the following steps to fix.

**Solution**:

- Log in to your cPanel account.
- Under **Preferences**, click **Change Password**.
- Type in your old password, and enter a new password (I had to enter a series of letters and numbers, so as not to make a dictionary word).
- Make sure **Allow MySQL password change** is selected.
- Click **Make Password Change Now**.


## How To Repair Mysql Database in WHM / Cpanel

You can attempt to repair MySQL databases using WebHost Manager.Then function checks each table for errors and tempts to fix them

- Login to WHM with https://yourserverip:2087
- At your left hand side pane ,Click on the Repair a Database link in the MySQL menu
- Click on the database that you want to repair in the displayed list and click on the Repair Database button.

A status list is displayed, stating which tables have been checked and the result.

## How to Set up Remote Mysql Server from WHM / Cpanel

You can change the  MySQL server from the local server (?localhost?) to point  to a remote server.This allows MySQL functions to be performed by another server.

To set up a remote MySQL  server

- Login to WHM with https://yourserverip:2087
- Click on the Setup Remote MySQL server link
- Enter the name of the remote  server in the Remote Mysql Host field and its pa ssword in the Remote Mysql Host‘s
- Root Password field.
- Click on the Setup button

**Note: Do not enter the root  password for the remote MySQL server in  the Remote Mysql Host‘s Root Passwordfield**


## PhpMyAdmin Error , Can not start Session

Cannot start session without errors, please  check errors given in your PHP and/or web server log file and configure your PHP installation properly.

There can be error in writing session files. Either the owner  do not have ?write‘ permission or the owner is different.

Normally tmp directories are used to dump sessions. And phpMyAdmin has its own tmp folder. Check the permission and ownership of this folder. Change it to the following

Location : /var/cpanel/userhomes/cpanel-phpmyadmin

cd /var/cpanel/userhomes/cpanel-phpmyadmin

- Permission of tmp must be 700
chmod 700 -R tmp
- Ownership must be cpanel-phpmyadmin
chown cpanel-phpmyadmin: -R *

The output should look similar to as given below

ll / var/cpanel/userhomes/cpanel-phpmyadmin 

drwx –x –x 4 cpanel-phpmyadmin cpanel-phpmyadmin 4096 Mar 10 23:56 ./
drwx –x –x 5 root root 4096 ../
drwxr-x—2 cpanel-phpmyadmin cpanel-phpmyadmin 4096 Mar 10 23:53 mail
drwx——2 cpanel-phpmyadmin cpanel-phpmyadmin 4096 Mar 10 23:56 tmp/ 


## Using myisamchk to Repair or Optimzie MySQL

If you run mysqld with external locking disabled (which is the default), you cannot reliably use myisamchk to check a table when mysqld is using the same table.If the server is run with external locking enabled, you can use myisamchk to check tables at any time. In this case, if the server tries to update a  table that myisamchk is using,  the server will wait for myisamchk to finish  before itcontinues.If you use myisamchk to repair or optimize tables, you must always ensure that the mysqld server is not using thetable (this also applies if external locking is disabled). If you do not stop mysqld, you should at least do amysqladmin flush-tables before you run myisamchk. Your tables may become corrupted if the server andmyisamchk access the tables simultaneously.When performing crash recovery, it is important to understand that each MyISAM table tbl_name in a databasecorresponds to the three files in the database directory shown in the following table.

File Purpose

- tbl_name.frm Definition (format) file
- tbl_name.MYD Data file
- tbl_name.MYI Index file

Each of these three file types is subject to corruption in various ways, but problems occur most often in data files and index files.

myisamchk works by creating a copy of the .MYD data file row by row. It ends the repair stage by removing the old.MYD file and renaming the new file to  the original file name.

myisamchk -e tbl_name

 
This does a complete and thorough check of all data (-e means ?extended check?).
It does a check -read of every keyfor each row to verify that they indeed point to the correct row.This may take a long time for a large table that hasmany indexes. Normally, myisamchk stops  after the first error it finds. If you want to  obtain more information, youcan add the -v (verbose) option. This causes myisamchk to keep going, up through a maximum of 20 error.

## How to Backup/Export and Restore/Import MySQL Database


**Exporting the Database**.

 In this example,we will export the ?testdb‘ database into  a file called ?testdb.sql‘:
 
Command : mysqldump -u root -p mydb  > mydb.sql

**Importing the Database**.

Importing the data is just as easy but involves two steps.The first step is to create a blank database ready to receive the data.

Command : mysqladmin -u root -p create testdb1

Once done, all that is  left is to actually import the data:
mysql -u root -p testdb1 < testdb.sq


## Mysql showing Socket Error in phpMyAdmin

While accessing phpMyAdmin, you ma y get the following error .

#**2002 - The server is not responding (or the local  MySQL server‘s socket is not correctly configured**)

This is due to the missing socket file in the location /tmp.

The socket path which  is specified in the phpM yAdmin configuration file is /tmp/mysql.sock.

vi /usr/local/cpanel/base/3rdparty/phpMyAdmin/config.inc.php cfg*'Server'+*'socket'+ = ‘/tmp/mysql.sock’;

If mysql.sock is missing in /tmp,  then create a link to the  mysql.sock file in /var/lib/mysql.

ln -s  /var/lib/mysql/mysql.sock /tmp/mysql.sock

**There is also another fix for this issue**.

1) Open the phpMyadmin config file ?config.inc.php

vi  /usr/local/cpanel/base/3rdparty/phpMyAdmin/config.inc.php

2) Locate the line

$cfg*'Servers'+*$i+*'host'+ = ‘localhost’;

3) Replace ?localhost‘ with ?127.0.0.1′ and save

$cfg*'Servers'+*$i+*'host'+ = ‘127.0.0.1';


## Mysql got error 28 from server handler

This error means no space left on hard disk. If you get his error, you need to check all filesystems where MySQL operates.

1) Stop mysql server

etc/init.d/mysql stop OR  /etc/init.d/mysqld stop

2) Check filesystem and /tmp  directories

$ df -h 
$ cd /tmp 
$ df -h /tmp

3) Remove files from /tmp to free up sp ace

#cd /tmp 
#rm -rf "contents that must be removed"

4) Look into /var/log directory and remove  or compress logs file

5) Use myisamchk command to check and repair of ISAM table

#cd /var/lib/mysql 
#myisamchk
6) Increase disk space (add new hard disk or remove unwanted softwares)

7) Start the mysql server:

#/etc/init.d/mysql start OR # /etc/init.d/mysqld start

## Mysql service fails to start with Error as "Cant init databases"


Following is the error message in  mysql server log file /var/log/mysqld.log

/usr/libexec/mysqld: Can’t create/write to file ‘/tmp/ibCfJwf1? (Errcode: 13)



While trying to start it, following is the error.

Initializing MySQL database: [ OK ] 

Timeout error occurred trying to start MySQL Daemon.

 Starting MySQL: [FAILED]

This error occurs when MySQL is  not able to access  the /tmp directory to write and create temporary files.  Make sure /tmp is owned by root and 1777 permisssion is set on /tmp director.

Following commands will fix the problem

#chown root:root /tmp
#chmod 777 /tmp 
#/etc/init.d/mysqld start

Now MySQL should start without a problem.

## How to change the Mysql database directory on server

Some times the ?/var‘ partition get crowded and we  might need to relocate the  database to some other location where
there is enough space. Below are the steps given for a trouble free relocation.

Note: Let ?/mysql‘ be the directory to which we want to relocate the database

Steps to change the mysql database directory

1) Execute the following command in the server to write the transactions saved in the memory to the hard disk

mysqladmin -u root -p  flush-tables

2) Stop the mysql process in the server

3) Move the database files to the the new directory

mv /var/lib/mysql/* /mysql

4) Create symlink with the old  directory

ln -s /test/mysql /var/lib/mysql/

5) Give the correct ownership  to the new directory

chown -R mysql:mysql /mysql/*

6) Restart mysql

## ACCESS DENIED CREATE DATABASE db_name' while importing a database

In order to solve this issue follow these steps:

   1)  Open the MySQL dump file with a text editor on your local workstation

   2)  Delete the line saying "CREATE DATABASE yourdbname". Usually this line is found at the very beginning of the file;

   3)  Save the file and try to import it again.
   
## How to change MySQL database collation?
   
1. Enter your cPanel and click on the phpMyAdmin icon in the Databases box.

2. Select the database you wish to manage from the drop-down menu on the left

3. Click on the Operations tab in the top menu of your phpMyAdmin

4.  At the bottom of the page you will see the collation option. You can now select a collation from the drop down menu and click on the Go button.

Please note that after your change the collation of a database only the new tables will be created with the new collation. All other tables remain with the collation, they were initially created.

## MySQL server has gone away' error in Application


This error happens when MySQL query you are trying to execute takes too long and the MySQL server times out.

You need to either optimize the database that is having this issue or you need to repair the database and its table

which you can do from cpanel itself

## How to optimize a MySQL database using phpMyAdmin?

log in to your phpMyAdmin and select the database whose tables you wish to optimize through Cpanel or WHM

A list with all the database's tables will appear. Tick the tables you wish to optimize.

From the  drop-down menu choose Optimize table. This will execute the OPTIMIZE TABLE SQL query on the selected tables and they will be updated and optimized.

## How to enable MySQL Native Driver (mysqlnd)

You can easily enable this. 

Login to server via SSH  as root user and create of edit the following file:

```
/var/cpanel/easy/apache/rawopts/all_php5
```

Add the following line to that file: ( If you're using mysqli)

```
--with-mysqli=mysqlnd
```
If not using mysqli, then use "--with-mysql=mysqlnd" instead.

Save the file, launch **EasyApache** and recompile as normal.  

Once done, run a PHP file with phpinfo() as the code to check the extension has been enabled.