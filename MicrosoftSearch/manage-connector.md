---
title: "Manage Microsoft Graph Connectors in the M365 Admin portal"
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
description: "Manage Microsoft Graph Connectors in the M365 Admin portal."
---

# Manage your connector in Microsoft 365 
To access and manage your connectors, you must be designated as a search administrator for your tenant. Contact your tenant administrator to provision you for the search administrator role.

## Get started
Navigate to the connectors management portal:
1.	Sign in to the [admin center](https://admin.microsoft.com).
2.	Go to **Settings** > **Microsoft Search** > **Connectors**.

For each connector type, the Microsoft 365 [admin center](https://admin.microsoft.com) supports the operations shown in the following table:

**Operation** | **Microsoft-built connector** | **Partner or custom-built connector**
--- | --- | ---
Add a connection | :heavy_check_mark: (See [configure your Microsoft-built connector](configure-connector.md)) | :x: (Refer to your partner or custom-built connector admin UX)
Delete a connection | :heavy_check_mark: | :heavy_check_mark:
Edit a published connection | :heavy_check_mark: Name<br></br> :heavy_check_mark: Description<br></br> :heavy_check_mark: Authentication credentials for your external data source<br></br> :heavy_check_mark: Gateway credentials for your on-premises data source<br></br> :heavy_check_mark: Refresh schedule<br></br> | :heavy_check_mark: Name<br></br> :heavy_check_mark: Description
Edit a draft connection | :heavy_check_mark: | :x:

## Monitoring your connection status
After creating the connection, the number of processed items will be displayed on the progress page.  (not progress bar) Once the initial full crawl is completed successfully, the progress for periodic incremental crawls will be shown.

Below are the four states that show up in the **Status** column against each connection:
* **Syncing**: the connector is crawling the data from the source to index the existing items and make any updates
* **Enabled**: the connection is enabled and there is no active crawl running against it. **Last sync time** indicates when the last successful crawl happened. The connection is as fresh as the time present there.
* **Paused**: the crawls are paused by the admins through the pause option. The next crawl will run only when it is manually resumed. However, the data from this connection will continue to be searchable.
* **Failed**: there was a critical failure in the connection. This requires manual intervention. The admin needs to take appropriate action based on the error message shown. Data which was indexed until the error occurred will be searchable.

## Preview limitations
* When you **publish** a Microsoft-built connector, it might take a few minutes for the connection to be created. During that time, the connection shows its status as pending. Also, there’s no auto-refresh, so you need to refresh manually.
* The Microsoft 365 [admin center](https://admin.microsoft.com) doesn’t support viewing and editing **search schema** after a connection is published. To edit a schema, delete your connection and then create a new one.
* When you manage your connection’s **refresh schedule**, the number of items that sync during each session are displayed. However, the sync history isn’t available.
