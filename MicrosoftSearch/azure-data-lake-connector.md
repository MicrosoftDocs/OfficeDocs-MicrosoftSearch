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
description: "Set up the Azure Data Lake Storage Gen2 Graph connector for Microsoft Search"
---

# Azure Data Lake Storage Gen2 Graph connector

With the Azure Data Lake Storage Gen2 connector, users in your organization can search for files stored in [Azure Blob Storage](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction) and [Azure Data Lake Gen 2 Storage](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction) accounts.

This article is for [Microsoft 365](https://www.microsoft.com/microsoft-365) administrators or anyone who configures, runs, and monitors an Azure Data Lake Storage Gen2 connector. It gives an overview of the connector configuration, capabilities, limitations, and troubleshooting techniques. In the article, we use *Azure Storage* as a generic term for [Azure Blob Storage](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction) and [Azure Data Lake Gen 2 Storage](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction).

## Step 1: Add a Graph connector in the Microsoft 365 admin center

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 2: Name the connection

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 3: Configure the connection settings

Enter your Primary storage connection String. This string is required to allow access to your storage account. To find your connection string, go to the [Azure portal](https://ms.portal.azure.com/#home) and navigate to the **Keys** section of your relevant Azure Storage account.

If you do not prefer to provide the **AccountKey** (a parameter in the primary storage connection string), you will need to grant access to our Graph Connectors Service for the following roles.

* Storage Blob Data Reader
* Storage Queue Data Contributor
* Storage Blob Delegator (only for hierarchical storage)

Navigate to the **Access Control** tab of your Azure Storage account, and follow the instructions there to grant access to the following app:

* **First Party App ID:** 56c1da01-2129-48f7-9355-af6d59d42766
* **First Party App Name:** Graph Connector Service

### Storage account and queue notifications (Optional)

Support to process changes in real time in the Graph Connectors Service might be added in the future. In that case, we'll monitor Azure Storage change notifications stored in a queue. You'll need to create a queue in the same account as your Azure Storage account.

After you create a queue, go to the **Events** tab on the queue page to configure **Event Subscription**. Choose all the Blob events that the queue will receive, and connect the queue to the Azure Storage account.

## Step 4: Assign property labels

You can assign a source property to each label by choosing from a menu of options. While this step is not mandatory, having some property labels will improve the search relevance and ensure more accurate search results for end users.## Manage search permissions

## Step 5: Manage schema

On the **Manage Schema** screen, you can change the schema attributes (the options are **Query**, **Search**, **Retrieve**, and **Refine**) associated with the properties, add optional aliases, and choose the **Content** property.

## Step 6: Manage search permissions

### Azure Data Lake Gen 2

On the **Manage search permissions** screen, you can choose to ingest the Access Control Lists (ACLs) from your [Azure Data Lake Gen 2 Storage](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction) account. When these search permissions are set, search content is trimmed based on the permissions assigned to the signed-in [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/) user searching the content. Alternatively, you can choose to make all the content indexed from your storage account visible to everyone in your organization. In this case, everyone in your organization will have access to all the data in your storage account.

The Azure Data Lake Storage Gen2 connector supports search permissions visible to **Everyone** or **Only people with access to this data source**. Indexed data that appears in the search results could be visible to all users in the organization or only to users who have access to each item.

### Azure Blob Storage

For a connection to [Azure Blob Storage](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction), all the content indexed from the configured source is visible to everyone in your organization. Access control lists are not supported at Blob level in Azure Blob Storage.

## Step 7: Set the refresh schedule

On the **Refresh Settings** screen, you can set the incremental crawl interval and the full crawl interval. The default intervals for the Azure Data Lake Storage Gen2 connector are 15 minutes for an incremental crawl and one week for a full crawl.

## Step 8: Review connection

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Limitations

A published connection for Azure Blob Storage cannot be reconfigured for Azure Data Lake Storage Gen2 source and vice-versa. In such scenarios, it is recommended to configure a new connection.

Also, the size of the files needs to be 4 MB or less for it to be crawled. File types currently supported are:

* Word (docx, .docm, .dotx, .dotm)
* PowerPoint (.pptm, .pptx, .potm, .potx, .ppam, .ppsm, .ppsx)
* Excel (.xlsx, .xlsm)
* Legacy Office formats (.doc, .dot, etc.)
* Text (.txt)
* HTML
* PDF

Binary files like images (.jpg, .bmp, etc.) are not supported. For example, if a .docx file contains only images, it might be skipped because it didn't return any content.
