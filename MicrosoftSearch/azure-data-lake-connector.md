---
title: "Azure Data Lake connector configuration in the M365 Admin portal"
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
description: "Azure Data Lake configuration in the M365 Admin portal."
---

# Azure Data Lake connector configuration in the M365 Admin portal

## Overview

The Azure Data Lake Storage Gen2 connector for Microsoft Search will allow your organization to search for files and their content stored in Azure Blob Containers and hierarchy enabled folders within a given Azure Data lake Storage Account. 

This article is intended for Microsoft Search Azure Data Lake Storage Gen2 connector administrators, or anyone who is responsible for configuring, running, and monitoring the connector. Here you can find information on what to know before configuring your connector, additional information regarding connector capabilities, and limitations.

## Things to know before configuring your connector

**Step** | **Details** | **Required/Optional?** 
Subscription Whitelisting | We need to whitelist customer’s Azure Subscription that has the Azure Data Lake Storage Gen 2 Account. This is needed to enable using Multi-Protocol Access based SDK to access the Azure Data Lake Storage Gen 2 Account. | Required
Granting Access | If you do not wish to provide us the Access Keys to their Azure Data Lake Gen 2 Storage account, you will need to grant read access to our GCS (Graph Connector Services) First Party Name in the Access Control tab of the ADLS (Azure Data Lake Storage Account).

**First Party App ID**: 56c1da01-2129-48f7-9355-af6d59d42766
**First Party App Name**: Graph Connector Service | Optional
Notification Storage Account and Queue | If in the future there is support added for processing changes near-real time in Graph Connector Services, we can monitor ADLS Change notifications stored in a queue. For this you will need to create a queue either in the same storage account where your ADLS Storage is, or you can use a different storage account and create a queue.

Once you have a queue, you can go to the Events Tab of the queue to configure Event Subscription where you can choose all the Blob events that the queue will receive as well as to connect the Queue to the ADLS Storage account. | Optional

## Connect to data source
On the authentication and config screen, please provide Primary Storage Connection String which is a required field for us to access your storage account. You can get this by going to the Azure Portal and navigating to the Keys section of the ADLS Storage account. Copy the connection string and paste it in here.

[](ADLS-connect2data.png)

## Search schema
On the Manage Schema screen, you can optionally change the queryable, searchable and retrievable properties of the File Schema that will be indexed from ADLS Storage Account.

[](ADLS-schema.png)

## Manage search permissions
On the Manage search permissions screen, you can choose to have us ingest the Access Control (ACLs) from your Storage account and do trimming of search content based on the currently logged in AAD User or make all the content indexed from your Storage Account visible to everyone in your organization.

[](ADLS-ACLs.png)

## Set refresh schedule 
On the Refresh Settings screen, you can set the incremental crawl interval and the full crawl intervals. The default is 15 minutes for the incremental crawl and 1 week for the full crawl. 

[](ADLS-refresh.png)

## Limitations
As of now, ADLS Gen 2 Multi-Protocol Access is only enabled in Central US, West Central US, Canada Central, East US, East Asis, North Europe, East US2, South East Asia, West Europe, West US, Australia East, Japan East, West US2 and Brazil South. Please refer to the documentation below for any updates.

## Additional information & resources
See [data lake storage multi-protocol access](https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-multi-protocol-access) for more information.



