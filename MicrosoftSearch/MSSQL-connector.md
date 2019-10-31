---
title: "Microsoft SQL connector configuration in the M365 Admin portal"
ms.author: v-pamcn
author: monaray
manager: mnirkhe
ms.date: 11/04/2019
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Microsoft SQL connector configuration in the M365 Admin portal."
---

# Configure a Microsoft SQL Server connector in Microsoft 365

With a Microsoft SQL Server connector for Microsoft Search, your organization can discover and index data from an on-premises SQL Server database. The connector indexes specified content into Microsoft Search. To keep the index up to date with source data, it supports periodic full and incremental crawls. With the SQL Server connector, you can also restrict access to search results for certain users.

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors a Microsoft SQL Server connector for Microsoft Search. It explains how to configure your connector and connector capabilities, limitations, and troubleshooting techniques.

## Install a data gateway
In order to access your third-party data, you must install and configure a Microsoft Power BI gateway. See [Install and on-premises gateway](https://docs.microsoft.com/en-us/data-integration/gateway/service-gateway-install) to learn more.  

## Connect to a data source
To connect a SQL Server connector to a data source, you must configure the database server you want crawled and the on-premises gateway. You can then connect to the database with the required authentication method.

> [!NOTE]
> Your database must run SQL Server version 2008 or later.

To search your database content, you must specify SQL queries when you configure the connector. These SQL queries need to name all the database columns that you want to index (i.e. source properties), including any SQL joins that need to be performed to get all the columns. To restrict access to search results, you must specify Access Control Lists (ACLs) with SQL queries when you configure the SQL Server connector.

## Full crawl (Required)
In this step, you configure the SQL query that runs a full crawl of the database. The full crawl selects all the columns or properties you want to be made **queryable**, **searchable**, or **retrievable**. You can also specify ACL columns to restrict access of search results to specific users or groups.

> [!Tip]
> To get all the columns that you need, you can join multiple tables.

![](media/MSSQL-fullcrawl.png)

### Select data columns (Required) and ACL columns (Optional)
The example demonstrates selection of five data columns that hold the data for the search: OrderId, OrderTitle, OrderDesc, CreatedDateTime, and IsDeleted. To set view permissions for each row of data, you can optionally select these ACL columns: AllowedUsers, AllowedGroups, DeniedUsers, and DeniedGroups. All these data columns can be made **queryable**, **searchable**, or **retrievable**.

Select data columns as shown in this example query: 
 `SELECT OrderId, OrderTitle, OrderDesc, AllowedUsers, AllowedGroups, DeniedUsers, DeniedGroups, CreatedDateTime, IsDeleted`

### Watermark (Required)
To prevent overloading the database, the connector batches and resumes full-crawl queries with a full-crawl watermark column. By using the value of the watermark column, each subsequent batch is fetched, and querying is resumed from the last checkpoint. Essentially this is a mechanism to control data refresh for full crawls.

Create query snippets for watermarks as shown in these examples:
* `WHERE (CreatedDateTime > @watermark)`. Cite the watermark column name with the reserved keyword `@watermark`. If the sort order of the watermark column is ascending, use `>`; otherwise, use `<`.
* `ORDER BY CreatedDateTime ASC`. Sort on the watermark column in ascending or descending order.

In the configuration shown in the following image, `CreatedDateTime` is the selected watermark column. To fetch the first batch of rows, specify the data type of the watermark column. In this case, the data type is `DateTime`.

![](media/MSSQL-watermark.png)

The first query fetches the first **N** amount of rows by using: "CreatedDateTime > January 1, 1753 00:00:00" (min value of DateTime data type). After the first batch is fetched, the highest value of `CreatedDateTime` returned in the batch is saved as the checkpoint if the rows are sorted in ascending order. An example is March 1, 2019 03:00:00. Then the next batch of **N** rows is fetched by using "CreatedDateTime > March 1, 2019 03:00:00" in the query.

### Skipping soft-deleted rows (Optional)
To exclude soft-deleted rows in your database from being indexed, specify the soft-delete column name and value that indicates the row is deleted.

![](media/MSSQL-softdelete.png)

## Incremental crawl (Optional)
In this optional step, provide a SQL query to run an incremental crawl of the database. With this query, the SQL Server connector makes any changes to the data since the last incremental crawl. As in the full crawl, select all columns that you want to be made **queryable**, **searchable**, or **retrievable**. Specify the same set of ACL columns that you specified in the full crawl query.

The components in the following image resemble the full crawl components with one exception. In this case, "ModifiedDateTime" is the selected watermark column. Review the [full crawl steps](#full-crawl-required) to learn how to write your incremental crawl query and see the following image as an example.

![](media/MSSQL-incrcrawl.png)

## Limitations
The Microsoft SQL connector has these limitations in the preview release:
* The on-premises database must run SQL Server version 2008 or later.
* ACLs are only supported by using a User Principal Name (UPN), Azure Active Directory (Azure AD), or Active Directory Security.
* Indexing rich content inside database columns is not supported. Examples of such content are HTML, JSON, XML, blobs, and document parsings that exist as links inside the database columns.

