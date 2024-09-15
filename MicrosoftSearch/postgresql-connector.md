---
ms.date: 09/12/2024
title: "PostgreSQL Microsoft Graph connector for Microsoft Search"
ms.author: vivg
author: vivg
manager: harshkum
audience: Admin
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
description: "Set up the PostgreSQL Microsoft Graph connector for Microsoft Search and Copilot"
---

# PostgreSQL Microsoft Graph connectors (Preview)

The PostgreSQL Microsoft Graph connector allows your organization to index records from a PostgreSQL database. After you configure the connector, end users can search for these records from PostgreSQL in Microsoft Copilot and from any Microsoft Search client.

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors a PostgreSQL Graph connector.

>[!NOTE]
>The PostgreSQL connector is in preview. If you wish to get early access to try it, sign up using [this form](https://forms.office.com/r/JniPmK5bzm).

## Capabilities
- Index records from your PostgreSQL database using a SQL query.
- Specify access permissions for every record with list of users or groups added in SQL query.
- Enable your end users to ask questions related to indexed records in Copilot.
- Use [Semantic search in Copilot](/MicrosoftSearch/semantic-index-for-copilot.md) to enable users to find relevant content based on keywords, personal preferences, and social connections.

## Limitations
- Supported PostgreSQL versions: The connector supports PostgreSQL version 14 or above.
- To support high crawl speed and better performance, the connector is built to support OLTP (Online Transaction Processing) workloads only. OLAP (Online Analytical Processing) workloads which do not execute the provided SQL query in 40 seconds timeout and aren't supported.
- ACLs are only supported by using a User Principal Name (UPN), Microsoft Entra ID, or Active Directory Security.
- Indexing rich content inside database columns isn't supported. Examples of such content are HTML, JSON, XML, blobs, and document parsings that exist as links inside the database columns.

## Prerequisites
- You must be the **search admin** for your organization's Microsoft 365 tenant.
- **Install the Microsoft Graph connector agent**: To access your PostgreSQL server, you must install and configure the connector agent. See [Install the Microsoft Graph connector agent](graph-connector-agent.md) to learn more.
- **PostgreSQL Server address**: To connect to your PostgreSQL data, you need your organization's PostgreSQL server address.
- **Service Account**: To connect to PostgreSQL server and allow Microsoft Graph Connector to update records regularly, you need a service account with read permissions granted to the service account.

## Get Started with Setup

### 1. Display name 
A display name is used to identify each citation in Copilot, helping users easily recognize the associated file or item. Display name also signifies trusted content. Display name is also used as a [content source filter](/MicrosoftSearch/custom-filters#content-source-filters). A default value is present for this field, but you can customize it to a name that users in your organization recognize.

### 2. PostgreSQL server
To connect to your PostgreSQL data, you need your PostgreSQL server address, port, and database name. 

### 3. Authentication Type
PostgreSQL connector only supports password based authentication to connect to the database.

### 4. Roll out to limited audience
Deploy this connection to a limited user base if you want to validate it in Copilot and other Search surfaces before expanding the roll out to a broader audience. To know more about limited rollout, [click here](staged-rollout-for-graph-connectors.md).

## Content
To search your database content, you must specify SQL queries when you configure the connector. These SQL queries need to name all the database columns that you want to index (source properties). This includes any SQL joins that need to be performed to get all the columns. To restrict access to search results, you must specify Access Control Lists (ACLs) within SQL queries when you configure the connector.

### 1. Full crawl (Required)

a. **Select data columns (Required) and ACL columns (Optional)** <br>

<details>
<summary>[Click to expand] Selecting data columns for full crawl query.</summary><br>

In this step, you configure the SQL query that runs a full crawl of the database. The full crawl selects all the columns or properties which need to be presented in Microsoft Copilot or Search. You can also specify ACL columns to restrict access of search results to specific users or groups.

> [!Tip]
> To get all the columns that you need, you can join multiple tables.

The example demonstrates a selection of five data columns that hold the data for the search: OrderId, OrderTitle, OrderDesc, CreatedDateTime, and IsDeleted. To set view permissions for each row of data, you can optionally select these ACL columns: AllowedUsers, AllowedGroups, DeniedUsers, and DeniedGroups. All these data columns also have the options to **Query**, **Search**, **Retrieve**, or **Refine**.

Select data columns as shown in this example query: 
 `SELECT OrderId, OrderTitle, OrderDesc, AllowedUsers, AllowedGroups, DeniedUsers, DeniedGroups, CreatedDateTime, IsDeleted`

The SQL connectors don't allow column names with non-alphanumeric characters  in the SELECT clause. Remove any non-alphanumeric characters from column names using an alias. Example - SELECT *column_name* AS *columnName*

To manage access to the search results, you can specify one or more ACL columns in the query. The SQL connector allows you to control access at per record level. You can choose to have the same access control for all records in a table. If the ACL information is stored in a separate table, you might have to do a join with those tables in your query.

The use of each of the ACL columns in the above query is described below. The following list explains the four **access control mechanisms**.

- **AllowedUsers**: This column specifies the list of user IDs who can access the search results.
- **AllowedGroups**: This column specifies the group of users who can access the search results.
- **DeniedUsers**: This column specifies the list of users who do **not** have access to the search results.
- **DeniedGroups**: This column specifies the group of users who do **not** have access to the search results.

</details> <br>

b. **Supported data types** <br>

<details>
<summary>[Click to expand] List of supported data types.</summary><br>

The table summarizes the SQL data types that are supported in the PostgreSQL connector. The table also summarizes the indexing data type for the supported SQL data type. To learn more about Microsoft Graph connectors supported data types for indexing, refer documentation on [property resource types](/graph/api/resources/property?preserve-view=true&view=graph-rest-beta#properties).

| Category | Source data type | Indexing data type |
| ------------ | ------------ | ------------ |
| Numeric | smallint <br> integer <br> bigint <br> smallserial <br> serial <br> bigserial | int64 |
| Numeric | decimal <br> numeric <br> real <br> double precision | double |
| Character | character varying(n) <br> varchar(n) <br> character(n) <br> char(n) <br> bpchar(n) <br> bpchar <br> text <br> | string |
| Monetary | money | int64 |
| Binary | bytea | string |
| Date or time | timestamp [(p)] without time zone <br> timestamp [(p)] with time zone <br> date <br> time [(p)] without time zone <br> time [(p)] with time zone | datetime |
| Date or time | interval [fields] [(p)] | string |
| Boolean | boolean | boolean |
| Enumerated | enum | string |

For any other data type currently not directly supported, the column needs to be explicitly cast to a supported data type.

</details> <br>

c. **Watermark (Required)** <br>

<details>
<summary>[Click to expand] Specifying the watermark column in full crawl query</summary><br>

To prevent overloading the database, the connector batches and resumes full-crawl queries with a full-crawl watermark column. By using the value of the watermark column, each subsequent batch is fetched, and querying is resumed from the last checkpoint. Essentially this mechanisms controls data refresh for full crawls.

Create query snippets for watermarks as shown in these examples:

- `WHERE (CreatedDateTime > @watermark)`. Cite the watermark column name with the reserved keyword `@watermark`. If the sort order of the watermark column is ascending, use `>`; otherwise, use `<`.
- `ORDER BY CreatedDateTime ASC`. Sort on the watermark column in ascending or descending order.

To fetch the first batch of rows, specify the data type of the watermark column.

The first query fetches the first **N** number of rows by using: "CreatedDateTime > January 1, 1753 00:00:00" (min value of DateTime data type). After the first batch is fetched, the highest value of `CreatedDateTime` returned in the batch is saved as the checkpoint if the rows are sorted in ascending order. An example is March 1, 2019 03:00:00. Then the next batch of **N** rows is fetched by using "CreatedDateTime > March 1, 2019 03:00:00" in the query.

</details> <br>

### 2. Soft delete instructions (Optional)

To exclude soft-deleted rows in your database from being indexed, specify the soft-delete column name and value that indicates the row is deleted.

## Users

### 1. Map columns containing access permissions information

Select **Map columns** to choose the various access control (ACL) columns that specify the access control mechanism. Select the column name you specified in the full crawl SQL query.

Each of the ACL columns is expected to be a multi-valued column. Separators such as semicolon (;), comma (,), and so on can separate these multiple ID values. You need to specify this separator in the **value separator** field.

The following ID types are supported for using as ACLs:

- **User Principal Name (UPN)**: A User Principal Name (UPN) is the name of a system user in an email address format. A UPN (for example: `john.doe@domain.com`) consists of the username (logon name), separator (the @ symbol), and domain name (UPN suffix).
- **Microsoft Entra ID**: In Microsoft Entra ID, every user or group has an object ID that looks something like 'e0d3ad3d-0000-1111-2222-3c5f5c52ab9b'.
- **Active Directory (AD) Security ID**: In an on-premises AD setup, every user and group have an immutable, unique security identifier that looks something like 'S-1-5-21-3878594291-2115959936-132693609-65242.'

### 2. Access permissions

You can choose to use the ACLs specified in the previous step or you can override them to make your content visible to everyone. 

## Sync
The refresh interval determines how often your data is synced between the data source and the Graph connector index.

You can configure full and incremental crawls based on the scheduling options present here. By default, incremental crawl (if configured) is set for every 15 minutes, and full crawl is set for every day. If needed, you can adjust these schedules to fit your data refresh needs.

At this point, you're ready to create the connection for PostgreSQL. You can click on the "Create" button to publish your connection and index data from your database.

## Troubleshooting
After publishing your connection, you can review the status under the **Data Sources** tab in the [admin center](https://admin.microsoft.com). To learn how to make updates and deletions, see [Manage your connector](manage-connector.md).

If you have any other issues or want to provide feedback, reach out to us at [Microsoft Graph | Support](https://developer.microsoft.com/en-us/graph/support)
