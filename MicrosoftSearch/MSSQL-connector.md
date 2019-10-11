---
title: "Microsoft SQL connector configuration in the M365 Admin portal"
ms.author: v-pamcn
author: TrishaMc1
manager: mnirkhe
ms.date: 10/08/2019
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Priority
search.appverid:
- BFB160
- MET150
- MOE150
description: "Microsoft SQL connector configuration in the M365 Admin portal."
---

# Microsoft SQL connector configuration in the M365 Admin portal

## Overview
The Microsoft (MS) SQL server connector for Microsoft Search will allow your organization to discover and index data from an on-premises MS SQL server database. The connector will ingest the specified content into the Microsoft search index and support periodic full and incremental crawl to keep the index up to date with the source. SQL server connector supports restricting access to the search results by specifying Access Control Lists (ACLs) while configuring the connector. 

This article is intended for Microsoft Search MS SQL connector administrators, or anyone who is responsible for configuring, running, and monitoring the connector. Here you can find information on what to know before configuring your connector, additional information regarding connector capabilities, and limitations.

## Things to know before configuring your connector
MS SQL server connector connects to the data source and traverses the content by issuing specified SQL queries during configuration. SQL queries need to enlist all the database columns the admin desires to index, including any SQL-joins which need to be performed to get all the columns. The SQL query also needs to specify the Access Control Lists (ACLs) which will be used to restrict access to the search results.

### Pre-requirements 
* The database needs to be running SQL server version 2008 or later. 
* An on-premises data gateway is required for configuring this connector. More details about the gateway can be found [here](https://docs.microsoft.com/en-us/power-bi/service-gateway-onprem). 

## Connect to data source
You need to configure the database server you want crawled and the on-premises data gateway with authentication to connect to the database.
( SHOULD WE ADD MORE INFO HERE ?????)

## Full crawl (required)
In this step, you need to configure the SQL query which will be executed for full crawl of the database. The full crawl selects all the columns you want to be made **queryable**, **searchable**, or **retrievable** (See [connector concepts](connectors-concepts.md) for more information on search schemas). Additionally, you can specify the ACL columns which you plan to use to restrict access of the search results to a specific set of users or groups.
>[TIP!]
>You may have to join multiple tables to get all the desired columns.

### Example
![](MSSQL-fullcrawl.png)

### Selected data columns (required) & ACL columns (optional)
The 5 data columns selected (OrderId, OrderTitle, OrderDesc, CreatedDateTime, IsDeleted) hold the data that the admin wishes to utilize for the search. The ACL columns (AllowedUsers, AllowedGroups, DeniedUsers, DeniedGroups) are optional but determine viewing permissions for each row of data. Any of these data columns can be made queryable, searchable, or retrievable. 

**Query snippet from the example**
“SELECT OrderId, OrderTitle, OrderDesc, AllowedUsers, AllowedGroups, DeniedUsers, DeniedGroups, CreatedDateTime, IsDeleted”

### Watermark (required)
A full-crawl watermark column is used by the connector to batch and resume full crawl queries to prevent overloading the database. The value of the watermark column will be used to fetch each subsequent batch and resume querying from the last checkpoint.

**Query snippets from the example**
* “WHERE (CreatedDateTime > @watermark)”: Mention the watermark column name with “@watermark” reserved keyword. If the sort order of watermark column is ascending, use “>” symbol, otherwise use “<” symbol. 
* “ORDER BY CreatedDateTime ASC”: Sort on watermark column in ascending or descending order. 

**Additional watermark configuration**
![](MSSQL-watermark.png)

In the above configuration, CreatedDateTime is the selected watermark column. The admin needs to specify the data type of watermark column to fetch the first batch of rows. In this case, the data type is 'DateTime'. 

The first query will fetch the first *n* many rows by using: “CreatedDateTime > January 1, 1753 00:00:00 (min value of DateTime data type)” in the query. After the first batch is fetched, the highest value of CreatedDateTime returned in the batch (assuming the rows are sorted in ascending order), say March 1, 2019 03:00:00, will be saved as the checkpoint. The next batch of *n* rows will be fetched using “CreatedDateTime > March 1, 2019 03:00:00” in the query.

### Skipping soft-deleted rows (optional)
If your database has rows that are soft-deleted and you want excluded from the search index, you need to specify the soft-delete column name and value that indicates the row is deleted.

![](MSSQL-softdelete.png)

## Incremental crawl (optional)
In this step, you can optionally configure the SQL query to execute an incremental crawl of the database. This allows the connector to make any changes to the data since the last incremental crawl. Like in the full crawl, you need to select all columns which you want to be made queryable, searchable, or retrievable. And you need to specify the same set of ACL columns which you specified in full crawl query. 

### Example
![](MSSQL-incrcrawl.png)

The above example has components that resemble the full crawl components with the following exception:
* ModifiedDateTime is the selected watermark column

## Limitations
* MS SQL server connector currently only supports an on-premises database running SQL server version 2008 or later. 
* Access Control Lists (ACLs) are supported only using User Principal Name (UPN), Azure Active Directory ID (AAD), or Active Directory Security ID (SID). 
( ADD LINKS ^^^^ ???)
* The connector does not support indexing rich content present inside the database columns such as HTML, JSON, XML, blobs, and document parsings present as links inside the database column.


