---
title: "Monitor Microsoft Graph connectors for Microsoft Search"
author: monaray97
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

To access and manage your Microsoft Graph connectors, you must be designated as a search administrator for your organization. Contact your administrator to assign you the search administrator role.

## Connection operations

In the [Microsoft 365 admin center](https://admin.microsoft.com), go to the [**connectors**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/Connectors).

For each connector type, the Microsoft 365 admin center supports the operations shown in the following table.

|Operation | Connectors by Microsoft | Connectors by partners
|:--- |:--- |:---|
|Add a connection | :heavy_check_mark: (see [Setup overview](configure-connector.md)) | :x: (refer to your partner or custom-built connector admin UX)|
|Delete a connection | :heavy_check_mark: | :heavy_check_mark:|
|Edit a published connection | :heavy_check_mark: Name and description<br></br> :heavy_check_mark: Connection settings<br></br> :heavy_check_mark: Property labels<br></br> :heavy_check_mark: Schema<br></br> :heavy_check_mark: Refresh schedule<br></br> | :heavy_check_mark: Name<br></br> :heavy_check_mark: Description|
|Edit a draft connection | :heavy_check_mark: | :x:|

## Monitor your connection state

This page provides insights into the connector's daily operations, as well as an overview of logs and error history. After creating a connection, the number of processed items is displayed on the **Connectors** tab of the **Microsoft Search** page. Once the initial full crawl is completed successfully, the progress of periodic incremental crawls is shown. 

The **State** column for each connection can display one of five statuses:

- Syncing - The connector crawls the data from the source to index the existing items and make any updates.
- Ready - The connection is ready, and there's no active crawl running against it. **Last sync time** indicates when the last successful crawl happened. The connection is as fresh as the last sync time.
- Paused - The crawls are paused by the admins through the pause option. The next crawl runs only when it's manually resumed. However, the data from this connection continues to be searchable.
- Failed - The connection had a critical failure. This error requires manual intervention. The admin needs to take appropriate action based on the error message shown. Data that was indexed until the error occurred is searchable. The next section talks about getting notified if such failures happen in a connection.
- Delete Failed - The deletion of the connection failed. Based on the failure reason, the data might still be indexed, item quota might still be consumed, and crawls might still run for the connection. We recommend that you try deleting the connection again in this state.

## Notifications for permanent crawl failures in your connections

Connection crawls are scheduled to run at specific intervals. Failures can occur due to various issues with the connections. Some failures are temporary, and crawls will resume automatically, while others are permanent and require administrative intervention to restart. In cases of permanent failures, the connection is marked as **Failed**, and notifications are sent to the service health dashboard under the section Issues for your organization to act on.

:::image type="content" alt-text="Screenshot that shows issues in your environment section of service health." source="media/manage-connector/shd-notification-home.png" lightbox="media/manage-connector/shd-notification-home.png":::

This information is also available as an advisory in the service status section of the service health page, under the Microsoft 365 suite category.

:::image type="content" alt-text="Screenshot that shows service status section" source="media/manage-connector/notification-service-status.png" lightbox="media/manage-connector/notification-bar-mac.png":::

If there are active notifications, admins receive alerts in the form of notification bars on the Microsoft Admin Center home page. These bars display the connection ID associated with the failed crawls. Admins can click on the notification bars to view more details or remove them from the page.

:::image type="content" alt-text="Screenshot that shows sample notification bar" source="media/manage-connector/notification-bar-mac.png" lightbox="media/manage-connector/notification-bar-mac.png":::

Admins can view the notification details by clicking the notification.

:::image type="content" alt-text="Screenshot that shows sample notification" source="media/manage-connector/sample-notification.png" lightbox="media/manage-connector/sample-notification.png":::

The notification remains active in the service health dashboard for six days. After this period, it is automatically moved to **Issue history** where it is retained for up to 30 days. If the connection resumes crawling, the notification is also moved to the Issue history. 
No new notification is issued for the same connection until crawling restarts. Should the crawls restart and fail again, a new notification is generated. For multiple connections with crawl failures, each connection has a separate notification bar on both the admin center home page and the service health dashboard landing page.

### Email notifications subscription

To receive failure notifications and updates via email, admins can add up to two email addresses. To configure this:

1. Navigate to the customize section on service health and open the email tab.
2. Check the box for **Issues in your environment that require action**.
3. In **Include these services**, select Microsoft 365 suite. It ensures that admins receive all notifications for the Microsoft 365 suite, including Microsoft Graph connector notifications, once they subscribe to service health notifications.
4. Save your changes.

:::image type="content" alt-text="Screenshot that shows e-mail subscription for notifications" source="media/manage-connector/notification-mail.png" lightbox="media/manage-connector/on-demand-crawl.png":::

## Manage crawls in your connections

During connection creation or edit connection flow, you can configure the crawl schedule through Refresh Settings. To learn more about the different types of crawls available see [Setup Overview](configure-connector.md).

Apart from the scheduled crawls, you can run on-demand crawls for your connection through the connection pane.

:::image type="content" alt-text="Screenshot that shows on-demand crawl connection pane." source="media/manage-connector/on-demand-crawl.png" lightbox="media/manage-connector/on-demand-crawl.png":::

On-demand crawl helps you start a crawl irrespective of the crawl schedule. You can choose to run a full or incremental crawl using the drop-down as shown in the image:

:::image type="content" alt-text="Screenshot that shows on-demand crawl drop-down." source="media/manage-connector/on-demand-dropdown.png" lightbox="media/manage-connector/on-demand-dropdown.png":::

> [!NOTE]
> The Microsoft Graph connector agent, only from version 2.1.0.0 onwards, supports on-demand crawl.

There can be only one category of crawl, scheduled or on-demand, running on a connection at any time. If a connection is in a "Syncing" state, on-demand crawls are disabled. Scheduled crawls are auto-triggered.

If a scheduled or an on-demand crawl continues beyond the time of the schedule of the next full or incremental crawl, the ongoing crawl is stopped, and the next scheduled crawl is skipped and queued. After the ongoing crawl completes, the crawl of the opposite type (full or incremental) is picked from the skipped queue and triggered. For example, if the previous crawl was of the type full crawl, only the incremental crawl, if present in the skipped queue, is triggered and vice versa.


* Identify connections that have some items that you didn't want to index. To update this connection, you must delete and create a new connection with a data source exclusion filter to exclude the items you don't want to index anymore.

* Permanently delete one or more connections.
