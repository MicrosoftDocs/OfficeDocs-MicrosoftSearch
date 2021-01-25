---
title: "Azure Data Lake Graph connector for Microsoft Search"
ms.author: monaray
author: monaray97
manager: shohara
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Set up the Azure Data Lake Storage Gen2 connector for Microsoft Search"
---

# Azure Data Lake Storage Gen2 Graph connector

With the Azure Data Lake Storage Gen2 connector, users in your organization can search for files stored in [Azure Blob Storage](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction) and [Azure Data Lake Gen 2 Storage](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction) accounts.

This article is for [Microsoft 365](https://www.microsoft.com/microsoft-365) administrators or anyone who configures, runs, and monitors an Azure Data Lake Storage Gen2 Graph connector. It gives an overview of the connector configuration, capabilities, limitations, and troubleshooting techniques. In the article, we use *Azure Storage* as a generic term for [Azure Blob Storage](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction) and [Azure Data Lake Gen 2 Storage](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction).

<!---## Before you get started-->

<!---Insert "Before you get started" recommendations for this data source-->

## Step 1: Add a Graph connector in the Microsoft 365 admin center

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup 
instructions.-->

## Step 2: Name the connection

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup 
instructions.-->

## Step 3: Configure the connection settings

Enter your Primary storage connection string. This string is required to allow access to your storage account. To find your connection string, go to the Azure portal and navigate to the **Keys** section of your relevant Azure Storage account.
If you don't want to provide the **AccountKey** (a parameter in the primary storage connection string), you'll need to grant access to our Graph Connectors Service for the following roles.

- Storage Blob Data Reader
- Storage Queue Data Contributor
- Storage Blob Delegator (only for hierarchical storage)

Navigate to the **Access Control** tab of your Azure Storage account, and follow the instructions there to grant access to the following app:

- **First Party App ID**: 56c1da01-2129-48f7-9355-af6d59d42766
- **First Party App Name**: Graph Connector Service

To monitor Azure Storage change notifications, enter your Azure Storage account name in the Notification queue name field.

## Step 4: Assign property labels

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup 
instructions.-->
Property labels help improve the search relevance and ensure more accurate search results for end users.

## Step 5: Manage schema

On the **Manage Schema** screen, you can change the schema attributes (**queryable**, **searchable**, **retrievable**, and **refinable**) associated with the properties, add optional aliases, and choose the **Content** property.

## Step 6: Manage search permissions

### Azure Data Lake Gen 2

On the Manage search permissions screen, you can choose to ingest the Access Control Lists (ACLs) from your Azure Data Lake Gen 2 Storage account. When these search permissions are set, search content is trimmed based on the permissions assigned to the signed-in Azure Active Directory user searching the content. Alternatively, you can choose to make all the content indexed from your storage account visible to everyone in your organization. In this case, everyone in your organization will have access to all the data in your storage account.

The Azure Data Lake Storage Gen2 connector supports search permissions visible to Everyone or Only people with access to this data source. Indexed data that appears in the search results could be visible to all users in the organization or only to users who have access to each item.

### Azure Blob Storage

For a connection to Azure Blob Storage, all the content indexed from the configured source is visible to everyone in your organization. Access control lists are not supported at Blob level in Azure Blob Storage.

## Step 7: Choose refresh settings

On the **Refresh Settings** screen, you can set the incremental crawl interval and the full crawl interval. The default intervals for the Azure Data Lake Storage Gen2 connector are 15 minutes for an incremental crawl and one week for a full crawl.

## Step 8: Review connection

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup 
instructions.-->

<!---## Troubleshooting-->
<!---Insert troubleshooting recommendations for this data source-->
## Limitations

A published connection for Azure Blob Storage cannot be reconfigured for Azure Data Lake Storage Gen2 source and vice-versa. In such scenarios, it is recommended to configure a new connection.
