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

Operation | Connectors by Microsoft | Connectors by partners
|:--- |:--- |:---
|Add a connection | :heavy_check_mark: (see [Setup overview](configure-connector.md)) | :x: (refer to your partner or custom-built connector admin UX)|
|Delete a connection | :heavy_check_mark: | :heavy_check_mark:|
|Edit a published connection | :heavy_check_mark: Name and description<br></br> :heavy_check_mark: Connection settings<br></br> :heavy_check_mark: Property labels<br></br> :heavy_check_mark: Schema<br></br> :heavy_check_mark: Refresh schedule<br></br> | :heavy_check_mark: Name<br></br> :heavy_check_mark: Description|
|Edit a draft connection | :heavy_check_mark: | :x:|

## Monitor your connection state

After you create a connection, the number of processed items shows on the **Connectors** tab on the **Microsoft Search** page. After the initial full crawl is completed successfully, the progress for periodic incremental crawls displays. This page provides information about the connector's day-to-day operations and an overview of the logs and error history.

Five states show up in the **State** column against each connection:

* **Syncing**. The connector crawls the data from the source to index the existing items and make any updates.

* **Ready**. The connection is ready, and there's no active crawl running against it. **Last sync time** indicates when the last successful crawl happened. The connection is as fresh as the last sync time.

* **Paused**. The crawls are paused by the admins through the pause option. The next crawl runs only when it's manually resumed. However, the data from this connection continues to be searchable.

* **Failed**. The connection had a critical failure. This error requires manual intervention. The admin needs to take appropriate action based on the error message shown. Data that was indexed until the error occurred is searchable. The next section talks about getting notified if such failures happen in a connection.

* **Delete Failed**. The deletion of the connection failed. Depending upon the failure reason, the data might still be indexed, item quota might still be consumed, and crawls might still run for the connection. We recommend that you try deleting the connection again in this state.

## Notifications for permanent crawl failures in your connections

The connection crawls are scheduled to run at specific times. The crawls can fail because of certain issues in the connections. Some times these issues are temporary and the crawls resume automatically and some times these failures are permanent where admin intervention is needed to start the crawls. In such cases of permanent failures, we mark the connection as "Failed" and send notifications to the Service Health Dashboard under the section: Issues for your organization to act on.

:::image type="content" alt-text="Screenshot that shows issues in your environment section of Service health." source="media/manage-connector/shd-notification-home.png" lightbox="media/manage-connector/shd-notification-home.png":::

The same can also be seen in the form of an advisory in the **Service status** section of the Service health page, under the Microsoft 365 suite category.

:::image type="content" alt-text="Screenshot that shows service status section" source="media/manage-connector/notification-service-status.png" lightbox="media/manage-connector/notification-bar-mac.png":::

If there are active notifications, admins get alerts in the form of notification bars on the Microsoft admin center home page. Notification bars contain the connection ID of the connection for which the crawls have failed. Admins can navigate to see more details of the notifications or remove the notification bars from the page.

:::image type="content" alt-text="Screenshot that shows sample notification bar" source="media/manage-connector/notification-bar-mac.png" lightbox="media/manage-connector/notification-bar-mac.png":::

Admins can check the notification details by clicking the notification.

:::image type="content" alt-text="Screenshot that shows sample notification" source="media/manage-connector/sample-notification.png" lightbox="media/manage-connector/sample-notification.png":::

Some points to note:

* The notification is live in the Service Health Dashboard for six days. After that, the notification is automatically moved to the "Issue History" section where the same is stored for a maximum of 30 days.
* If the connection resumes the crawl, the notification is automatically moved to the "Issue History" section.
* No new notification is sent for the same connection until the crawls on that connection restart. Once the crawls are restarted and if a failure happens again, a new notification is sent.
* If there are crawl failures in multiple connections, each connection has a separate notification bar in the admin center home page and service health dashboard landing page.

### Subscribing for getting notifications in e-mail

To get these failure notifications and updates on the e-mail, admins can add up to two e-mail addresses for the same.

* Go to the Customize section on the Service health page and open the email tab.
* Select the check box for - Issues in your environment that require action.
* In the "Include these services" section, select Microsoft 365 suite. Admins get all notifications for the Microsoft 365 suite, including Microsoft Graph connector notifications, after they subscribe to the service health notifications.
* Save

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
