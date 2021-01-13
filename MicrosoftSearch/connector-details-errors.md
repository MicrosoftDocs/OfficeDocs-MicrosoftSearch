---
title: "Connectors Details and Errors"
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
description: "Connectors Details and Errors"
---
<!-- markdownlint-disable no-inline-html -->

# View Connection Details and Errors for Microsoft Search

To access and manage your connectors, you must be designated as a search administrator for your tenant. Contact your tenant administrator to provision you for the search administrator role.

Navigate to the [Connectors tab](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/Connectors) in the [Microsoft 365 admin center](https://admin.microsoft.com).

You can view connection details and errors when you click on the connection on the [Connectors tab](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/Connectors).  

## View your last crawl info

After the first initial incremental or full crawl completes successfully, the last crawl data values are displayed under the last crawl header in the detail pane. If there was no last crawl that ran, you will not see any information under the last crawl header. This information about last crawl will help you gain insights into how the crawl performed and take necessary steps wherever required.

The following last crawl values will be available for each connection:

Value | Description
--- | ---
**Completed at** | Date and time the last crawl got completed
**Type** | Incremental or full crawl
**Duration** | how much time did the last crawl take to complete
**Successes** | Number of items that have been successfully ingested in the last crawl
**Errors** | Number of items that errored in the last crawl

## Monitor errors

For each **Active Connector** on the **Connectors** tab, any existing crawl errors show under the **Error** tab. The tab lists error codes, the count of each, and error log download options. See the example in the following image. Select an **error code** to view the error's details.

![Connectors list with a connector selected and details pane showing 3 errors for this connector.](media/errormonitoring1.png)

To view an error's specific details, select its error code. A screen appears with error details and a link. The most recent errors appear at the top. See the example in the following table.

![Connector list with a connector selected and details pane showing the list of errors for the connector.](media/errormonitoring2.png)

Below is the list of different errors that can appear against any connection. If these solutions don’t work, contact support or send us [feedback](connectors-feedback.md).

Error code | Error message | Solution
--- | --- | ---
1000 | The data source isn't available. Check your internet connection or make sure the data source is still accessible by the connector. | This error occurs when the data source is not reachable due to a network issue or when the data source itself is deleted, moved, or renamed. Check if the data source details provided are still valid.
1001 | Can't update the data, because the data source is throttling the connector. | To unthrottle the data source, check if its scale limits can be increased or wait until a less traffic-heavy time of the day.
1002 | Can't authenticate with the data source. Verify that the credentials associated with this data source are correct. | Click **Edit** to update the authentication credentials.
1003 | The account associated with the connector doesn't have permission to access the item. |  Ensure the proper account has access to the item you want indexed.
1004 | Unable to reach the on-premises data gateway. Make sure the gateway service is running and the gateway details are updated in the connection configuration. | Check the computer with the gateway, open the Power BI Gateway application and make sure the gateway is running. Verify that the gateway is using the same admin account as Microsoft Search, then make sure all the gateway details are all updated in the connection configuration.
1005 | Credentials associated with this data source have expired. Renew the credentials and update the connection. | Click **Edit** to update the authentication credentials.
1006 | Your gateway version is out of date and doesn’t support this connector anymore. You will need to update the gateway. | Please visit [Install an on-premises data gateway](https://docs.microsoft.com/data-integration/gateway/service-gateway-install) to download  and install the latest version of the Power BI gateway on the machine containing the gateway.
1007 | No valid Power BI license detected. You need a valid Power BI license to perform this crawl. | You need a valid Power BI license to perform this crawl. Check that your organization has a valid license. If it does, try again. If it doesn’t, obtain a license and then try again.
1008 | The total quota utilization of your tenant has reached its limit. | Try deleting a connection to free up some of your quota or adjusting your ingestion filters to bring in less data. If these don't solve the issue, contact Microsoft support.
1009 | The total quota utilization for your connection has reached its limit. | Try adjusting your ingestion filters to bring in less data. If this doesn't solve the issue, contact Microsoft support.
1010 | The total quota utilization for indexing non-Azure AD groups has reached its limit of 100K. | Try deleting a connection to free up some of your quota or adjusting your ingestion filters to bring in less data. If these don't solve the issue, contact Microsoft support.
1011 | The Graph connector [agent](on-prem-agent.md) is not reachable or offline. | 
1012 | Authentication to your connection failed due to an unsupported authentication mode. | Edit the connection to update the authentication settings for your connection.
2001 | Indexing is throttled because of a large number of updates in the queue. Depending on the queue, it can take some time for the updates to complete. | Please wait until the queue gets cleared.
2002 | Indexing failed due to unsupported item formatting. | See connector-specific documentation for more information.
2003 | Indexing failed due to unsupported item content. | See connector-specific documentation for more information.
2004 | Indexing failed due to unsupported item or file size. | See connector-specific documentation for more information.
2005 | Indexing failed because the URI is too long. | See connector-specific documentation for more information.
2006 | User mapping failed due to an invalid mapping formula or no Azure AD user with this property. | Try deleting and recreating the connection with a different mapping formula. 
2007 | This item will not be displayed in Microsoft Search because some users or groups without permission to view this item could not be indexed. | 
2008 | Connections can't have non-Azure AD groups with more than 50,000 members. | Try removing users from a group or try removing items ACLed with that group from ingestion and recreate the connection.
2009 | Non-Azure AD group indexing is temporarily paused due to a large number of requests. Indexing will resume when the system finishes processing these requests. Please check back later. | 
2010 | This connection is no longer valid because of an update made by Microsoft. Please delete the connection and create a new one. | Please delete the connection and create a new one.
5000 | Something went wrong. If this continues, contact support. |
