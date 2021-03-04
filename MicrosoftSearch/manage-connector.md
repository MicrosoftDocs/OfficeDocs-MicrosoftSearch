---
title: "Manage Microsoft Graph Connectors for Microsoft Search"
ms.author: monaray
author: monaray97
manager: mnirkhe
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Manage Microsoft Graph Connectors for Microsoft Search."
---
<!-- markdownlint-disable no-inline-html -->

# Monitor your connections

To access and manage your connectors, you must be designated as a search administrator for your tenant. Contact your tenant administrator to provision you for the search administrator role.

## Connection Operations

Navigate to the [Connectors tab](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/Connectors) in the [Microsoft 365 admin center](https://admin.microsoft.com).

For each connector type, the [Microsoft 365 admin center](https://admin.microsoft.com) supports the operations shown in the following table:

Operation | Graph connectors by Microsoft | Partner or Graph connectors
--- | --- | ---
Add a connection | :heavy_check_mark: (See [Setup overview](configure-connector.md)) | :x: (Refer to your partner or custom-built connector admin UX)
Delete a connection | :heavy_check_mark: | :heavy_check_mark:
Edit a published connection | :heavy_check_mark: Name and Description<br></br> :heavy_check_mark: Connection settings<br></br> :heavy_check_mark: Property labels<br></br> :heavy_check_mark: Schema<br></br> :heavy_check_mark: Refresh schedule<br></br> | :heavy_check_mark: Name<br></br> :heavy_check_mark: Description
Edit a draft connection | :heavy_check_mark: | :x:

## Monitor your connection status

After you create a connection, the number of processed items shows on the **Connectors** tab on the **Microsoft Search** page. After the initial full crawl completes successfully, the progress for periodic incremental crawls displays. This page provides information about the connector's day-to-day operations and an overview of the logs and error history.

Four states show up in the **Status** column against each connection:

* **Syncing**. The connector is crawling the data from the source to index the existing items and make any updates.

* **Enabled**: The connection is enabled, and there's no active crawl running against it. **Last sync time** indicates when the last successful crawl happened. The connection is as fresh as the last sync time.

* **Paused**. The crawls are paused by the admins through the pause option. The next crawl runs only when it's manually resumed. However, the data from this connection continues to be searchable.

* **Failed**. The connection had a critical failure. This error requires manual intervention. The admin needs to take appropriate action based on the error message shown. Data that was indexed until the error occurred is searchable.

## Monitor your index quota utilization

The available index quota and consumption is displayed on the connectors landing page.

![Index quota utilization bar](media/quota_utilization.png)

>[!NOTE]
>During the preview period, every organization trying out Graph connectors was provided a free fixed quota of up to 2 million items across all connections. With Graph connectors being generally available, the free quota will expire on April 1st, 2021 for those organizations who have been using Graph connectors in preview.
>Microsoft-built Graph connectors labeled as ["Preview"](connectors-preview.md) will not be included in the total charged index quota for your organization. However, it will count towards the max number of 10 connections you can configure for your organization and the max number of 7 million items your organization can index across connections; each connection is limited 700,000 items. 

The quota utilization bar will indicate various states based on consumption of quota by your organization:

State | Quota consumption
--- | ---
Normal | 1-69%
High | 70-89%
Critical | 90%-99%
Full | 100%

The number of items indexed will also be displayed with each connection. The number of items indexed by each connection contributes to the total quota available for your organization.

When index quota is exceeded for your organization, all active connections will be impacted, and those connections will operate in **limit exceeded** state. In this state, your active connections  

* Will not be able to add new items.

* Will be able to update or delete existing items.

To fix this, you can do any of the following:

* Learn how to purchase index quota for your organization at [Licensing requirements and pricing](licensing.md).

* Identify connections which have too much content being ingested and update them to index fewer items to make room for quota. To update the connection, you must delete and create a new connection with a new ingestion filter which brings in fewer items.

* Permanently delete one or more connections
