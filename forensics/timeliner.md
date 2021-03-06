---
layout: forensics
category: forensics
title: Timeliner
---

# {{ page.title }} #

## Info ##

Timerliner is is designed to improve time line analysis for the output produced by the excellent log2timeline. There are plans to add support for log2timeline's replacement plaso in the near future once the release is stable.

The viewing and sorting of CSV files via spreadsheet software generally does not work well due to the volumes of data involved in modern time line analysis, which is where Timeliner comes in. The earlier releases of Timeliner used SQL Server LocalDB, which was fast but had a 10 GB database size limit, which became a problem when I tried to import a 15 million event time line! 

The implementation has it's limitations e.g. to support that amount of events and still perform fast queries I have had to remove support for jumping to page X etc, but it means it will page through the results taking under 1 second for 20000 results, under 3 for 100,000 results. The new query mechanism has meant I have had to remove the ability to apply custom sorts, a default sort on the time stamp is added by default. 

## Features ##

- Imports log2timeline, ntfswalk and fls
- Fast querying (under 1 second for 20000 results, under 3 seconds for 100,000 results)
- Supports huge data sets (tested with 15 million events)

## Third party ##
- [CsvHelper](https://github.com/JoshClose/CsvHelper): CSV output
- [LumenWorks.Framework.IO.Csv](http://www.codeproject.com/Articles/9258/A-Fast-CSV-Reader): Fast CSV reading
- [NLog](http://github.com/NLog/NLog) : Logging
- [Npgsql](http://npgsql.projects.pgfoundry.org/): Postgres driver for .Net
- [NPoco](https://github.com/schotime/NPoco): Data access
- [ObjectListView](http://objectlistview.sourceforge.net/cs/index.html) : Data viewing via lists 
- [protobuf-net](https://code.google.com/p/protobuf-net/): Extracting data from Plaso storage objects
- [Utility](http://www.woanware.co.uk): Misc functions (woanware)

## Requirements ##

Microsoft .NET Framework v4.5 

## Installation/Running ##
 
- Install [postgres](http://www.postgresql.org/download/) database on the local machine 
- Open pgadmin and connect to the server, enter the password set during the installation
- Right click on the Database treeview node and select "New Database"
- Enter the database name as 'timeliner' (note that casing is important with postgres) and then click OK 
- Then expand the databases node, and select the new 'timeliner' database
- Next click the SQL icon on the toolbar, this will open the SQL query window
- Copy the contents of the SQL script (schema.sql) located in the Database folder into the SQL query window or just drag the file onto the window
- Then press the green arrow button on the toolbar or press F5 to execute the query, this should create the schema and set the appropriate permissions
- Next run Timeliner, create a new project, and import your time line file

## Download ##

- [Source Code](https://github.com/woanware/Timeliner)
- [Binaries (v0.1.2)](/downloads/Timeliner.v0.1.2.zip) 