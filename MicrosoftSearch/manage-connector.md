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

# Manage Microsoft Graph Connectors in the M365 Admin portal

In order to get access to manage your connectors, you must be designated as a search administrator for your tenant. If you are not a search administrator, you must contact your tenant administrator to provision you for this role.

To navigate to the connectors management portal, do the following:
1.	Sign into the admin portal: https://admin.microsoft.com.
2.	Go to **Settings** > **Microsoft Search** > **Connectors**. 

The following operations are supported in the Microsoft 365 admin portal for each connector type:

**Operations** | **Microsoft built-in connector** | **Partner connector** | **Custom-built connector**
--- | --- | --- | ---
Add a connection | :heavy_check_mark: <br></br> (See [Configure your Microsoft built-in connector](configure-connector.md)) | :x: <br></br> (Contact your partner) | :x:
Delete a connection | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:
Edit a published connection | <li>:heavy_check_mark: Name</li><li>:heavy_check_mark: Description</li><li>:heavy_check_mark: Authentication credentials for your external data source</li><li>:heavy_check_mark: Gateway credentials for your on-premises data source</li><li>:heavy_check_mark: Refresh schedule</li> | <li>:heavy_check_mark: Name</li><li>:heavy_check_mark: Description</li> | <li>:heavy_check_mark: Name</li><li>:heavy_check_mark: Description</li>
Edit a draft connection | :heavy_check_mark: | :x: | :x: 


> [!NOTE]
> * When publishing a Microsoft built-in connector, it may take a few minutes for the connector to be confirmed. In the interim, the connector will show its status as pending. And during this time, auto-refresh is not enabled, and thus you need to manually refresh.
> * The connectors admin portal does not support viewing and editing of your search schema once the connection has been published. If you choose to edit the schema, you must first delete your connection then create a new one.


