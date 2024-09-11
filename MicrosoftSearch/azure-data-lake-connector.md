---
ms.date: 10/08/2019
title: "Azure Data Lake Microsoft Graph connector for Microsoft Search"
ms.author: mecampos
author: mecampos
manager: umas
audience: Admin
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
description: "Set up the Azure Data Lake Storage Gen2 Microsoft Graph connector for Microsoft Search"
---
<!---Previous ms.author: monaray --->

# Azure Data Lake Storage Gen2 Microsoft Graph connector

The Azure Data Lake Storage Gen2 Microsoft Graph connector allows users in your organization to search for files stored in [Azure Blob Storage](/azure/storage/blobs/storage-blobs-introduction) and [Azure Data Lake Gen 2 Storage](/azure/storage/blobs/data-lake-storage-introduction) accounts.

> [!NOTE]
> Read the [**Setup your Microsoft Graph connector**](configure-connector.md) article to understand the general connectors setup instructions.

This article is for anyone who configures, runs, and monitors an Azure Data Lake Storage Gen2 connector. It supplements the general setup process, and shows instructions that apply only for the Azure Data Lake Storage Gen2 connector. This article also includes information about [Limitations](#limitations).

In the article, we use *Azure Storage* as a generic term for [Azure Blob Storage](/azure/storage/blobs/storage-blobs-introduction) and [Azure Data Lake Gen 2 Storage](/azure/storage/blobs/data-lake-storage-introduction).

## Step 1: Add a connector in the Microsoft 365 admin center

[Add Azure Data Lake Storage Gen2 connector](https://admin.microsoft.com/adminportal/home#/MicrosoftSearch/Connectors/add?ms_search_referrer=MicrosoftSearchDocs_ADLSGen2&type=ADLSGen2)

(See general [setup instructions](./configure-connector.md) for more details)
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 2: Name the connection

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 3: Configure the connection settings

Enter your primary storage connection string. This string is required to allow access to your storage account. To find your connection string, go to the [Azure portal](https://ms.portal.azure.com/#home) and navigate to the **Keys** section of your relevant Azure Storage account.

If you prefer not to provide the **AccountKey** (a parameter in the primary storage connection string), grant access to the Microsoft Graph connectors service for the following roles:

* Storage Blob Data Reader
* Storage Queue Data Contributor
* Storage Blob Delegator

Navigate to the **Access Control** tab of your Azure Storage account, and follow the instructions there to grant access to the following app:

* **First Party App ID:** 56c1da01-2129-48f7-9355-af6d59d42766
* **First Party App Name:** Graph Connector Service

### Storage account and queue notifications (Optional)

Support to process changes in real time in the Graph Connectors Service might be added in the future. In that case, we'll monitor Azure Storage change notifications stored in a queue. You'll need to create a queue in the same account as your Azure Storage account.

After you create a queue, go to the **Events** tab on the queue page to configure **Event Subscription**. Choose all the Blob events that the queue will receive, and connect the queue to the Azure Storage account.

### Test the connection

Test the connection by clicking the **Test Connection** button

> [!NOTE]
> The **Test Connection** must succeed before you can move to the next configuration section. The ADLS gen 2 enabled storage account **MUST** have a Container **AND** at least one file within it as a minimum for the **Test Connection** to succeed. A connection error will be raised if the content does not exist.

## Step 4: Assign property labels

You can assign a source property to each label by choosing from a menu of options. While this step isn't mandatory, having some property labels will improve the search relevance and ensure better search results for end users.

## Step 5: Manage schema

On the **Manage Schema** screen, you can change the schema attributes associated with the properties, the options are **Query**, **Search**, **Retrieve**, and **Refine**. You also can add optional aliases, and choose the **Content** property.

## Step 6: Manage search permissions

### Azure Data Lake Gen 2

You can choose to ingest the Access Control Lists (ACLs) from your [Azure Data Lake Gen 2 Storage](/azure/storage/blobs/data-lake-storage-introduction) account. When these search permissions are set, search content is trimmed based on the permissions of the user signed in [Microsoft Entra ID](/azure/active-directory/). Alternatively, you can choose to make all the content indexed from your storage account visible to everyone in your organization. In this case, everyone in your organization will have access to all the data in your storage account.

The Azure Data Lake Storage Gen2 connector supports search permissions visible to **Everyone**, or **Only people with access to this data source**. Indexed data that appears in the search results could be visible to users in the organization who have access to each item.

### Azure Blob Storage

For a connection to [Azure Blob Storage](/azure/storage/blobs/storage-blobs-introduction), all the content indexed from the configured source is visible to everyone in your organization. Access control lists aren't supported at Blob level in Azure Blob Storage.

## Step 7: Set the refresh schedule

On the **Refresh Settings** screen, you can set the incremental crawl interval and the full crawl interval. The default intervals for the Azure Data Lake Storage Gen2 connector are 15 minutes for an incremental crawl and one week for a full crawl.

## Step 8: Review connection

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

<!---## Troubleshooting-->
<!---Insert troubleshooting recommendations for this data source-->

## Limitations

A published connection for Azure Blob Storage cannot be reconfigured for Azure Data Lake Storage Gen2 source and the other way around. In such scenarios, it's recommended to configure a new connection.

Also, the size of the files needs to be 4 MB or less for it to be crawled. File types currently supported are:

* Word (docx, .docm, .dotx, .dotm)
* PowerPoint (.pptm, .pptx, .potm, .potx, .ppam, .ppsm, .ppsx)
* Excel (.xlsx, .xlsm)
* Legacy Office formats (.doc, .dot, etc.)
* Text (.txt)
* HTML
* PDF

Binary files like images (.jpg, .bmp, etc.) are not supported. For example, if a .docx file contains only images, it might be skipped because it didn't return any content.


## Troubleshooting
After publishing your connection, you can review the status under the **Data Sources** tab in the [admin center](https://admin.microsoft.com). To learn how to make updates and deletions, see [Manage your connector](manage-connector.md).

You can find troubleshooting steps for commonly seen issues [here](troubleshoot-azure-data-lake-connector.md).

If you have any other issues or want to provide feedback, write to us [aka.ms/TalkToGraphConnectors](https://aka.ms/TalkToGraphConnectors).
