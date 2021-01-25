---
title: "Microsoft SQL server and Azure SQL connector for Microsoft Search"
ms.author: vivg
author: Vivek
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Set up the Microsoft SQL connector for Microsoft Search."
---

# Azure SQL and Microsoft SQL server Graph connectors

With a Microsoft SQL server or Azure SQL connector, your organization can discover and index data from an on-premises SQL Server database or a database hosted in your Azure SQL instance in the cloud. The connector indexes specified content into Microsoft Search. To keep the index up to date with source data, it supports periodic full and incremental crawls. With these SQL connectors, you can also restrict access to search results for certain users.

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors a Microsoft SQL server or Azure SQL connector. It supplements the general instructions provided in the [Set up your Graph connector](https://docs.microsoft.com/microsoftsearch/configure-connector) article. If you have not already done so, read the entire Setup your Graph connector article to understand the general setup process.

Each step in the setup process is listed below along with either a note that indicates you should follow the general setup instructions OR other instructions that apply to only Microsoft SQL server and Azure SQL connectors. This article also includes information about Limitations for Microsoft SQL server and Azure SQL connector.

## Before you get started

### Install the Graph connector agent (required for on-premises Microsoft SQL server connector only)

In order to access your on-premises third-party data, you must install and configure the Graph connector agent. See [Install the Graph connector agent](on-prem-agent.md) to learn more.  

## Step 1: Add a Graph connector in the Microsoft 365 admin center

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup 
instructions.-->

## Step 2: Name the connection

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup 
instructions.-->

## Step 3: Configure the connection settings

### Register an app (for Azure SQL connector only)

For Azure SQL connector, you must register an app in Azure Active Directory to allow Microsoft Search app to access data for indexing. To learn more about registering an app, refer Microsoft Graph documentation on how to [register an app](https://docs.microsoft.com/graph/auth-register-app-v2).

After completing the app registration and taking note of the app name, application (client) ID and tenant ID, you need to [generate a new client secret](https://docs.microsoft.com/azure/healthcare-apis/register-confidential-azure-ad-client-app#application-secret). The client secret will only be displayed once. Remember to note & store the client secret securely. Use the client ID and client secret while configuring a new connection in Microsoft Search.

To add the registered app to your Azure SQL Database, you need to:

- Log in to your Azure SQL DB
- Open a new query window
- Create a new user by running the command ‘CREATE USER [app name] FROM EXTERNAL PROVIDER’
- Add user to role by running command 'exec sp_addrolemember 'db_datareader', [app name]'
   Or
   'ALTER ROLE db_datareader ADD MEMBER [app name]'

>[!NOTE]
>To revoke access to any app registered in Azure Active Directory, refer the Azure documentation on [removing a registered app](https://docs.microsoft.com/azure/active-directory/develop/quickstart-remove-app).

### Connection settings

To connect your Microsoft SQL server connector to a data source, you must configure the database server you want crawled and the on-prem agent. You can then connect to the database with the required authentication method.

> [!NOTE]
> Your database must run SQL server version 2008 or later for the Microsoft SQL server connector to be able to connect.

For the Azure SQL connector, you only need to specify the server name or IP address you want to connect to. Azure SQL connector only supports Azure Active Directory Open ID connect (OIDC) authentication to connect to the database.

For added security, you may configure IP firewall rules for your Azure SQL server or database. To learn more about setting up IP firewall rules, refer documentation on [IP firewall rules](https://docs.microsoft.com/azure/azure-sql/database/firewall-configure). Add the following client IP ranges in the firewall settings.

| Region | IP Range |
| ------------ | ------------ |
| NAM | 52.250.92.252/30, 52.224.250.216/30 |
| EUR | 20.54.41.208/30, 51.105.159.88/30 |
| APC | 52.139.188.212/30, 20.43.146.44/30 |

To search your database content, you must specify SQL queries when you configure the connector. These SQL queries need to name all the database columns that you want to index (that is, source properties), including any SQL joins that need to be performed to get all the columns. To restrict access to search results, you must specify Access Control Lists (ACLs) within SQL queries when you configure the connector.

## Step 3a: Full crawl (Required)

In this step, you configure the SQL query that runs a full crawl of the database. The full crawl selects all the columns or properties you want to be made **queryable**, **searchable**, or **retrievable**. You can also specify ACL columns to restrict access of search results to specific users or groups.

> [!Tip]
> To get all the columns that you need, you can join multiple tables.

![Script showing the OrderTable and AclTable with example properties](media/MSSQL-fullcrawl.png)

### Select data columns (Required) and ACL columns (Optional)

The example demonstrates selection of five data columns that hold the data for the search: OrderId, OrderTitle, OrderDesc, CreatedDateTime, and IsDeleted. To set view permissions for each row of data, you can optionally select these ACL columns: AllowedUsers, AllowedGroups, DeniedUsers, and DeniedGroups. All these data columns can be made **queryable**, **searchable**, or **retrievable**.

Select data columns as shown in this example query: 
 `SELECT OrderId, OrderTitle, OrderDesc, AllowedUsers, AllowedGroups, DeniedUsers, DeniedGroups, CreatedDateTime, IsDeleted`

To manage access to the search results, you can specify one or more ACL columns in the query. The SQL connector allows you to control access at per record level. You can choose to have the same access control for all records in a table. If the ACL information is stored in a separate table, you might have to do a join with those tables in your query.

The use of each of the ACL columns in the above query is described below. The following list explains the four **access control mechanisms**.

- **AllowedUsers**: This column specifies the list of user IDs who can access the search results. In the following example, list of users: john@contoso.com, keith@contoso.com, and lisa@contoso.com would only have access to a record with OrderId = 12.
- **AllowedGroups**: This column specifies the group of users who will be able to access the search results. In the following example, group sales-team@contoso.com would only have access to record with OrderId = 12.
- **DeniedUsers**: This column specifies the list of users who do **not** have access to the search results. In the following example, users john@contoso.com and keith@contoso.com do not have access to record with OrderId = 13, whereas everyone else has access to this record.
- **DeniedGroups**: This column specifies the group of users who do **not** have access to the search results. In the following example, groups engg-team@contoso.com and pm-team@contoso.com do not have access to record with OrderId = 15, whereas everyone else has access to this record.  

![Sample data showing the OrderTable and AclTable with example properties](media/MSSQL-ACL1.png)

### Supported data types

The below table summarizes the SQL data types that are supported in the MS SQL and Azure SQL connectors. The table also summarizes the indexing data type for the supported SQL data type. To learn more about Microsoft Graph connectors supported data types for indexing, refer documentation on [property resource types](https://docs.microsoft.com/graph/api/resources/property?view=graph-rest-beta#properties).

| Category | Source data type | Indexing data type |
| ------------ | ------------ | ------------ |
| Date and time | date <br> datetime <br> datetime2 <br> smalldatetime | datetime |
| Exact numeric | bigint <br> int <br> smallint <br> tinyint | int64 |
| Exact numeric | bit | boolean |
| Approximate numeric | float <br> real | double |
| Character string | char <br> varchar <br> text | string |
| Unicode character strings | nchar <br> nvarchar <br> ntext | string |
| Other data types | uniqueidentifier | string |

For any other data type currently not directly supported, the column needs to be explicitly cast to a supported data type.

### Watermark (Required)

To prevent overloading the database, the connector batches and resumes full-crawl queries with a full-crawl watermark column. By using the value of the watermark column, each subsequent batch is fetched, and querying is resumed from the last checkpoint. Essentially this mechanisms controls data refresh for full crawls.

Create query snippets for watermarks as shown in these examples:

- `WHERE (CreatedDateTime > @watermark)`. Cite the watermark column name with the reserved keyword `@watermark`. If the sort order of the watermark column is ascending, use `>`; otherwise, use `<`.
- `ORDER BY CreatedDateTime ASC`. Sort on the watermark column in ascending or descending order.

In the configuration shown in the following image, `CreatedDateTime` is the selected watermark column. To fetch the first batch of rows, specify the data type of the watermark column. In this case, the data type is `DateTime`.

![Watermark column configuration](media/MSSQL-watermark.png)

The first query fetches the first **N** number of rows by using: "CreatedDateTime > January 1, 1753 00:00:00" (min value of DateTime data type). After the first batch is fetched, the highest value of `CreatedDateTime` returned in the batch is saved as the checkpoint if the rows are sorted in ascending order. An example is March 1, 2019 03:00:00. Then the next batch of **N** rows is fetched by using "CreatedDateTime > March 1, 2019 03:00:00" in the query.

### Skipping soft-deleted rows (Optional)

To exclude soft-deleted rows in your database from being indexed, specify the soft-delete column name and value that indicates the row is deleted.

![Soft delete settings: "Soft delete column" and "Value of soft delete column which indicates a deleted row"](media/MSSQL-softdelete.png)

### Full crawl: Manage search permissions

Select **Manage permissions** to choose the various access control (ACL) columns that specify the access control mechanism. Select the column name you specified in the full crawl SQL query.

Each of the ACL columns is expected to be a multi-valued column. These multiple ID values can be separated by separators such as semicolon (;), comma (,), and so on. You need to specify this separator in the **value separator** field.

The following ID types are supported for using as ACLs:

- **User Principal Name (UPN)**: A User Principal Name (UPN) is the name of a system user in an email address format. A UPN (for example: john.doe@domain.com) consists of the username (logon name), separator (the @ symbol), and domain name (UPN suffix).
- **Azure Active Directory (AAD) ID**: In Azure AD, every user or group has an object ID that looks something like ‘e0d3ad3d-0000-1111-2222-3c5f5c52ab9b’.
- **Active Directory (AD) Security ID**: In an on-premises AD setup, every user and group have an immutable, unique security identifier that looks something like ‘S-1-5-21-3878594291-2115959936-132693609-65242.’

![Search permission settings to configure access control lists](media/MSSQL-ACL2.png)

## Step 3b: Incremental crawl (Optional)

In this optional step, provide a SQL query to run an incremental crawl of the database. With this query, the SQL connector determines any changes to the data since the last incremental crawl. As in the full crawl, select all columns that you want to be made **queryable**, **searchable**, or **retrievable**. Specify the same set of ACL columns that you specified in the full crawl query.

The components in the following image resemble the full crawl components with one exception. In this case, "ModifiedDateTime" is the selected watermark column. Review the [full crawl steps](###Step-3a:-Full-crawl-(Required)) to learn how to write your incremental crawl query and see the following image as an example.

![Incremental crawl script showing OrderTable, AclTable and example properties that can be used.](media/MSSQL-incrcrawl.png)

## Step 4: Assign property labels

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).

<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup 
instructions.-->

## Step 5: Manage schema

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup 
instructions.-->

## Step 6: Manage search permissions

You can choose to use the [ACLs specified in the full crawl screen](#full-crawl-manage-search-permissions) or you can override them to make your content visible to everyone.

## Step 7: Choose refresh settings

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup 
instructions.-->

## Step 8: Review connection

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup 
instructions.-->

## Next steps: Customize the search results page

Create your own verticals and result types, so end users can view search results from new connections. Without this step, data from your connection won’t show up on the search results page.

To learn more about how to create your verticals and MRTs, see [Search results page customization](customize-search-page.md).

<!---## Troubleshooting-->

<!---Insert troubleshooting recommendations for this data source-->

## Limitations

The SQL connectors have these limitations in the preview release:

- Microsoft SQL server connector: The on-premises database must run SQL server version 2008 or later.
- ACLs are only supported by using a User Principal Name (UPN), Azure Active Directory (Azure AD), or Active Directory Security.
- Indexing rich content inside database columns is not supported. Examples of such content are HTML, JSON, XML, blobs, and document parsings that exist as links inside the database columns.
