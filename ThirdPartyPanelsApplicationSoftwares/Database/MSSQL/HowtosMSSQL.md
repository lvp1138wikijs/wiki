---
title: How tos MSSQL
description: 
published: true
date: 2021-04-27T16:33:04.416Z
tags: 
editor: markdown
dateCreated: 2021-04-27T16:33:04.416Z
---

# How do I configure a DSN to connect to my MS SQL Express

**To configure a DSN, please follow these steps**:

1) Log into your server through Remote Desktop Connection

2) Click Start, Programs, Administrative Tools, and select Data Sources (ODBC).

3) On the SystemDSN tab, click Add.

4) Scroll through the list of drivers and select SQL Server

5) Click Finish

6) Enter the requested information

- Name: enter the name for the DSN
- Description: enter a description for the DSN (Optional)
- Server: enter the IP address of your server, followed by \SQLEXPRESS
7) Click Next

8) Enter the requested information

- Select With SQL Server authentication
- Login ID: enter the SQL username for the database
- Password: enter the SQL password for the database
9) Click Client Configuration

10) Uncheck Dynamically determine port and set the Port number to 1433

11) Click OK

12) Click the Next button twice and then click Finish

13) Click Test Data Source to ensure the data source is configured properly

14) Once the test completes, click OK



# How do I configure MS SQL Express Server to allow remote connections?

1) Log into your server through Remote Desktop Connection

2) Click Start, Programs, Microsoft SQL Server 2005 and select SQL Server Management Studio

3) Enter the requested information

- Server Type: select Database Engine
- Server Name: this field should be populated by default
- Authentication: select Windows Authentication
4) Click Connect

5) Right click the server name and select Properties

6) Click Security

7) Under Server authentication select SQL Server and Windows Authentication Mode

8) Click OK

9) Right click the server name and select Restart. Wait a few moments for the service to restart before proceeding

10) Click Start, Programs, Microsoft SQL Server 2005, Configuration Tools and select SQL Server Surface Area Configuration

11) Click Surface Area Configuration for Services and Connections

12) Expand SQL Server Browser

13) Change the startup type to Automatic and click Apply

14) Click Start

15) Click OK


# How do I enable mixed mode authentication in MS SQL?


1) Log into your server through Remote Desktop Connection

2) Click Start, Programs, Microsoft SQL Server and select SQL Server Management Studio Express or SQL Server Management Studio, depending on your version of SQL Server.

3) Enter the requested information

- Server Type: select Database Engine
- Server Name: this field should be populated by default
- Authentication: select Windows Authentication

4) Click Connect

5) Right click the server name and select Properties

6) Click Security

7) Under Server authentication select SQL Server and Windows Authentication Mode

8) Click OK

9) Right click the server name and select Restart. Wait a few moments for the service to restart before proceeding

# How to Identify SQL Injection

Identifying SQL Injection is fairly easy. Commonly you may have received complaints of the site attempting to load malware on visitors' computers. This is because the injection attack has inserted tags into the database fields that load externally linked javascript. Typically the site will not have any obvious visual clues of attack, however the performance of the site may be degraded. If you view the source of the site and search for ".js" you will quickly find the injected scripts.

You have now identified that the site has indeed been SQL injected. The database may need to be restored. You will need to investigate further to find out when the attack started to you can restore the appropriate backup (a clean one).

**Faster SQL Injection identification**

- Open the site up in Firefox
- Open up FireBug
- First screen in firebug shows the load times of all files and requests made due to the current page load. Look in the second column for a domain name that is suspicious.
- View the source of the page and find that domain name. If it is in a <script src="URL HERE"></script> format, then it is likely SQL injection.
- Open up the database and run the stored procedure below. If it returns the number of corrections, you have just cleaned there database of one string. Be sure to refresh the page in Firefox and double check that there aren't other strings that have been injected.

```

CREATE PROC SearchAndReplace

(

    @SearchStr nvarchar(1000),

    @ReplaceStr nvarchar(1000)

)

AS

BEGIN

    SET NOCOUNT ON

    DECLARE @TableName nvarchar(256), @ColumnName nvarchar(128), @tColumnName nvarchar(128), @SearchStr2 nvarchar(110), @SQL nvarchar(4000), @RCTR int

    SET @TableName = ''

    SET @SearchStr2 = QUOTENAME('%' + @SearchStr + '%','''')

    SET @RCTR = 0

    WHILE @TableName IS NOT NULL

    BEGIN

        SET @ColumnName = ''

        SET @tColumnName = ''

        SET @TableName =

        (

            SELECT MIN(QUOTENAME(TABLE_SCHEMA) + '.' + QUOTENAME(TABLE_NAME))

            FROM     INFORMATION_SCHEMA.TABLES

            WHERE         TABLE_TYPE = 'BASE TABLE'

                AND    QUOTENAME(TABLE_SCHEMA) + '.' + QUOTENAME(TABLE_NAME) > @TableName

                AND    OBJECTPROPERTY(

                        OBJECT_ID(

                            QUOTENAME(TABLE_SCHEMA) + '.' + QUOTENAME(TABLE_NAME)

                             ), 'IsMSShipped'

                         ) = 0

        )

        WHILE (@TableName IS NOT NULL) AND (@ColumnName IS NOT NULL)

        BEGIN

            SET @ColumnName =

            (

                SELECT MIN(QUOTENAME(COLUMN_NAME))

                FROM     INFORMATION_SCHEMA.COLUMNS

                WHERE         TABLE_SCHEMA    = PARSENAME(@TableName, 2)

                    AND    TABLE_NAME    = PARSENAME(@TableName, 1)

                    AND    DATA_TYPE IN ('char', 'varchar', 'nchar', 'nvarchar')

                    AND    QUOTENAME(COLUMN_NAME) > @ColumnName

            )

            IF @ColumnName IS NOT NULL

            BEGIN

                SET @SQL=    'UPDATE ' + @TableName +

                        ' SET ' + @ColumnName

                        + ' = REPLACE(' + @ColumnName + ', '

                        + QUOTENAME(@SearchStr, '''') + ', ' + QUOTENAME(@ReplaceStr, '''') +

                        ') WHERE ' + @ColumnName + ' LIKE ' + @SearchStr2

                EXEC (@SQL)

                SET @RCTR = @RCTR + @@ROWCOUNT

            END

        END    

WHILE (@TableName IS NOT NULL) AND (@tColumnName IS NOT NULL)

        BEGIN

            SET @tColumnName =

            (

                SELECT MIN(QUOTENAME(COLUMN_NAME))

                FROM     INFORMATION_SCHEMA.COLUMNS

                WHERE         TABLE_SCHEMA    = PARSENAME(@TableName, 2)

                    AND    TABLE_NAME    = PARSENAME(@TableName, 1)

                    AND    DATA_TYPE IN ('ntext', 'text')

                    AND    QUOTENAME(COLUMN_NAME) > @tColumnName

            )

            IF @tColumnName IS NOT NULL

            BEGIN

                SET @SQL=    'UPDATE ' + @TableName +

                        ' SET ' + @tColumnName

                        + ' = REPLACE(cast(' + @tColumnName + ' AS NVARCHAR(Max)), '

                        + QUOTENAME(@SearchStr, '''') + ', ' + QUOTENAME(@ReplaceStr, '''') +

                        ') WHERE ' + @tColumnName + ' LIKE ' + @SearchStr2

                EXEC (@SQL)

                SET @RCTR = @RCTR + @@ROWCOUNT

            END

        END    

    END

    SELECT 'Replaced ' + CAST(@RCTR AS varchar) + ' occurrence(s)' AS 'Outcome'

END

```

Once you have confirmed that the site has been attacked, it is important to take ALL of the following steps to ensure that the issue is properly handled.

- Find out when the attack started. It is common for an attack to go unnoticed for several days. This is because, as stated earlier, the site may not have any obvious visual indications of attack.
- Secure a clean backup of the database.

Although the above may seem like a lot of work it can be accomplish in very little time with the right tools. Once you are familiar with the process, it may only take you 15-20 minutes to complete the entire process


# SQL Server Tuning 

Although tuning a database is fairly easy, you can make things worse if you don't know what you're doing. Be careful when performing this.

**Check the DB_ID**

- Create an account in SQL that has sysadmin rights. This user is to be removed upon completion of the tuning
- From your workstation, use Management Studio tpo log into the database server using a sysadmin SQL user
- Expand databases, right-click the database you'll be profiling and select New Query
- Note: If you're using Enterprise Manager, go to Tools > SQL Query Analyzer
- Execute the following query:
- 
- SELECT DB_ID() 
- Remeber the DB_ID number that was returned


**Run a trace on the DB**

1. From your workstation, open SQL Profiler
1. Choose File >> New Trace >> Connect
1. Connect with the SQL sysadmin user you created earlier, this will open the Trace properties window
1. Choose the General tab

-    Specify a Trace Name
-    From the Use the template dropdown box select Tuning
-    Select the checkbox for Save to file
       - Specify a location to save your trace to in the popup window
       
5. Choose the Events Selection Tab

- Select the Checkbox for Show all columns
- Keep the existing Data Columns events selected and add these additional ones:

    -CPU
    -Reads
    -Writes
    
  -Click Column Filters
   -Select DatabaseID from tjhe left side, expand Equals from the right side and specify the DB_ID from the previous section.
6. Click Run
7. Stop the trace after about 50,000-75,000 rows of data, or 1 hour - whichever comes first. See the notes below for reference while that is running.

-    There is no correct number of events to capture or a correct amount of time to run the trace. As a general rule of thumb, get anywhere from 50,000-75,000 rows of data or 1 hour, whichever comes first.
-    For very active databases it's best to ask someone with more experience for some help.
-    It's very important to trace during a good time, not during backups - but likely during the time when the database is busiest.
   
While the trace is running, keep the following in mind:

# Run the Tuning Advisor

This will put a heavy load on the server but should be performed during peak times in order to ensure accurate tuning results.  

If you have a really small workload (say, less the 1MB) then you can do this whenever you want only if you keep an eye on performance on the db server to ensure it doesn't cause an unreasonable CPU spike or slows I/O too much.

1. Open the Database Engine Tuning Advisor
   Programs >> SQL Server 2005 >> Performance Tools
1. Connect with the SQL sysadmin user you created earlier
1. On the General tab
1. Ensure the File radio button is selected in the Workload section.
1. Click on the little binoculars button to locate the trace file(s) you created in the previous section
1. From the Database for workload analysis drop down box select the database you are tuning.
1. Select only the checkbox next to the database you are profiling at bottom of the screen.
1. If you are running this late at night uncheck the Limit tuning timecheck box, otherwise, during the day keep it checked (and don't forget to monitor db server performance!!).

- Click the Start Analysis button and wait for the tuning recommendations to complete.
- When the tuning completes go to the Actions menu and choose Save Recommendations.
  - Save it to a location where it will be available for a week or so. You probably won't need the file but it's always good to keep it around for a week or two after the tune in case something needs to be rolled back.
- From the Actions select Apply Recommendations.

Note what % increase in performance the tuner said it would give, this is a theoretical improvement and what you will see from the application will likely not match the theoretical DB performance improvement.

**Cleanup**

Remove the sysadmin user you created in the first section

# Determining when SQL Server 2008 was Last Restarted

1) Launch SQL Server Management Studio

2) Click New Query

3) Enter the following query

SELECT create_date
FROM sys.databases
WHERE database_id = 2 --TEMPDB's database_id

4) Click Execute

5) The last restarted date is displayed under Results

# Back up all MS SQL databases at once

This article will discuss how to backup all MS SQL databases with one script. A separate file will be created for each database.

- Log into your server through Remote Desktop Connection
- Open SQL Server Management Studio and select the server name
- Click the New Query button and enter in the following data:

DECLARE @name VARCHAR(50) -- database name

DECLARE @path VARCHAR(256) -- path for backup files

DECLARE @fileName VARCHAR(256) -- filename for backup

DECLARE @fileDate VARCHAR(20) -- used for file name

SET @path = 'C:\Backup\' 

SELECT @fileDate = CONVERT(VARCHAR(20),GETDATE(),112)

DECLARE db_cursor CURSOR FOR

SELECT name

FROM master.dbo.sysdatabases

WHERE name NOT IN ('master','model','msdb','tempdb')

OPEN db_cursor

FETCH NEXT FROM db_cursor INTO @name

WHILE @@FETCH_STATUS = 0

BEGIN

SET @fileName = @path + @name + '_' + @fileDate + '.BAK'

BACKUP DATABASE @name TO DISK = @fileName

FETCH NEXT FROM db_cursor INTO @name

END

CLOSE db_cursor

DEALLOCATE db_cursor 

1. Make sure that the directory in the SET @path line exists. If the directory (in this case C:\Backup) does not exist, create the directory else the script will fail
1. Click the Execute! button and the script will execute
1. Once finished, a dialog box will appear stating such. Now all databases are backed up in C:\Backup with the database name as the file name
 
 