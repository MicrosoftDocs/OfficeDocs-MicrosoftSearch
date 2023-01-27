---
title: "Monitor Microsoft Graph connectors for Microsoft Search"
ms.author: mecampos
author: monaray97
manager: mnirkhe
audience: Admin
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
description: "Monitor your connection state and index quota utilization."
ms.date: 10/08/2019
---

# Monitor your connections

To access and manage your Microsoft Graph connectors, you must be designated as a search administrator for your tenant. Contact your tenant administrator to provision you for the search administrator role.

## Connection operations

In the [Microsoft 365 admin center](https://admin.microsoft.com), go to the [**Connectors** tab](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/Connectors).

For each connector type, the Microsoft 365 admin center supports the operations shown in the following table.

Operation | Connectors by Microsoft | Connectors by partners
--- | --- | ---
Add a connection | :heavy_check_mark: (see [Setup overview](configure-connector.md)) | :x: (refer to your partner or custom-built connector admin UX)
Delete a connection | :heavy_check_mark: | :heavy_check_mark:
Edit a published connection | :heavy_check_mark: Name and description<br></br> :heavy_check_mark: Connection settings<br></br> :heavy_check_mark: Property labels<br></br> :heavy_check_mark: Schema<br></br> :heavy_check_mark: Refresh schedule<br></br> | :heavy_check_mark: Name<br></br> :heavy_check_mark: Description
Edit a draft connection | :heavy_check_mark: | :x:

## Monitor your connection state

After you create a connection, the number of processed items shows on the **Connectors** tab on the **Microsoft Search** page. After the initial full crawl completes successfully, the progress for periodic incremental crawls displays. This page provides information about the connector's day-to-day operations and an overview of the logs and error history.

Five states show up in the **State** column against each connection:

* **Syncing**. The connector is crawling the data from the source to index the existing items and make any updates.

* **Ready**. The connection is ready, and there's no active crawl running against it. **Last sync time** indicates when the last successful crawl happened. The connection is as fresh as the last sync time.

* **Paused**. The crawls are paused by the admins through the pause option. The next crawl runs only when it's manually resumed. However, the data from this connection continues to be searchable.

* **Failed**. The connection had a critical failure. This error requires manual intervention. The admin needs to take appropriate action based on the error message shown. Data that was indexed until the error occurred is searchable.

* **Delete Failed**. The deletion of the connection failed. Depending upon the failure reason, the data might still be indexed, item quota might still be consumed, and crawls might still run for the connection. We recommend that you try deleting the connection again in this state.

## Monitor your index quota utilization

The available index quota and consumption is displayed on the connectors landing page.

:::image type="content" alt-text="Index quota utilization bar." source="media/quota_utilization.png" lightbox="media/quota_utilization.png":::

The quota utilization bar indicates various states based on consumption of quota by your organization:

State | Quota utilization levels
--- | --- 
Normal | 0&ndash;79%
High | 80&ndash;89%
Critical | 90%&ndash;99%
Full | 100%

The number of items indexed is also displayed with each connection. The number of items indexed by each connection contributes to the total quota available for your organization.

When index quota is exceeded for your organization, all active connections are impacted, and those connections operate in a **limit exceeded** state. In this state, your active connections:  

* Will **not** be able to add new items.

* Are able to update or delete existing items.

To fix this, you can do any of the following actions:

* Purchase index quota for your organization, to learn more see: [Licensing requirements and pricing](licensing.md).

* Identify connections that have some items which you did not want to index. To update this connection, you must delete and create a new connection with a data source exclusion filter to exclude the items you do not want to index anymore.

* Permanently delete one or more connections.
