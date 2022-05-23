---
title: "Microsoft Graph connectors view details and errors"
ms.author: monaray
author: monaray97
manager: mnirkhe
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
description: "Access and manage your Microsoft Graph connectors as a search administrator for your tenant."
---
<!-- markdownlint-disable no-inline-html -->

# View your connection details and errors

To access and manage your Microsoft Graph connectors, you must be designated as a search administrator for your tenant. Contact your tenant administrator to provision your account for the search administrator role.

To see your connections in the [Microsoft 365 admin center](https://admin.microsoft.com), go to the [Data sources tab](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/connectors).

You can view the connection details and errors by selecting the connection.  

:::image type="content" source="media/datasourcestab.png" alt-text="Connectors list with a connector selected and details pane showing information about this connector.":::

## View your last crawl info

After the first initial incremental or full crawl completes successfully, the last crawl data values are displayed under the last crawl header in the detail pane. If there was no last crawl that ran, you don't see any information under the last crawl header. This information about the last crawl helps you gain insights into how the crawl performed, and allows you to take necessary steps wherever required.

The following last crawl values are available for each connection:

Value | Description
--- | ---
**Completed at** | Date and time the last crawl got completed
**Type** | Incremental or full crawl
**Duration** | How much time the last crawl took to complete
**Successes** | Number of items that have been successfully ingested in the last crawl
**Errors** | Number of items that produced an error in the last crawl

## Monitor errors

For each **Active Connector** on the **Data sources** tab, any existing crawl errors show under the **Current crawl** header, in the **Errors** section. It lists error codes, the count of each, and error log download options. You can select an **error code** to view the error's details.

:::image type="content" source="media/errormonitoring1.png" alt-text="Details pane showing the current crawl, and errors section for the selected connector.":::

To view an error's specific details, select its error code. A screen appears with error details and a link. The most recent errors appear at the top.

The following list shows the different errors that can appear against any connection.

Error code | Error message | Solution
--- | --- | ---
1000 | The data source isn't available. Check your internet connection or make sure the data source is still accessible by the connector. | This error occurs when the data source isn't reachable due to a network issue or when the data source itself is deleted, moved, or renamed. Check if the data source details provided are still valid.
1001 | Can't update the data because the data source is throttling the connector. | To unthrottle the data source, check if its scale limits can be increased or wait until a less traffic-heavy time of the day.
1002 | Can't authenticate with the data source. Verify that the credentials associated with this data source are correct. | Select **Edit** to update the authentication credentials.
1003 | The account associated with the connector doesn't have permission to access the item. |  Ensure the proper account has access to the item you want indexed.
1005 | Credentials associated with this data source have expired. Renew the credentials and update the connection. | Select **Edit** to update the authentication credentials.
1008 | The total quota utilization of your tenant has reached its limit. | Try deleting a connection to free up some of your quota or adjusting your ingestion filters to bring in less data. If these steps don't solve the issue, contact Microsoft support.
1009 | The total quota utilization for your connection has reached its limit. | Try adjusting your ingestion filters to bring in less data. If this step doesn't solve the issue, contact Microsoft support.
1010 | The total quota utilization for indexing non-Azure AD groups has reached its limit of 100 K. | Try deleting a connection to free up some of your quota or adjusting your ingestion filters to bring in less data. If these steps don't solve the issue, contact Microsoft support.
1011 | The Microsoft Graph connector [agent](graph-connector-agent.md) isn't reachable or offline. |
1012 | Authentication to your connection failed due to an unsupported authentication mode. | Edit the connection to update the authentication settings for your connection.
1015 | Connections created on this agent will fail due to insufficient permissions. Grant the ExternalItem.ReadWrite.OwnedBy  permission to the Microsoft Azure app used for registration to allow the app to read and write all external items without a signed-in user and resume the crawl. | Ensure that the Azure app used for Agent registration has ExternalItem.ReadWrite.OwnedBy  permission.
1016 | Connections created on this agent will fail due to insufficient permissions. Grant the Directory.Read.All  permission to the Microsoft Azure app used for registration to read data in your organization's directory and resume the crawl.
 | Ensure that the Azure app used for Agent registration has  Directory.Read.All permission.
1017 | Item can't be indexed because the network is unavailable. | Restore the network and wait for the next crawl for the item to get indexed.
1018 | Please ensure that the entered user account has interactive logon rights to the machine where Graph connector agent is installed. | Ensure that the user account has interactive logon rights to the machine where Graph connector agent is installed. Refer [documentation](./graph-connector-agent#connection-failure) to learn more.
1019 | Connection failed because the app credentials given to GCA instance are invalid or expired. Please update the credentials. | Check your app credentials for GCA instance associated with the connection.
1020 | Graph connector agent associated with the connection is not able to connect to GRPC connector server. | The GCA instance could not crawl the datasource as there was an issue with connecting to the custom connector over GRPC.
1025 | Graph Connector Agent associated with this connection is deprecated due to critical issues, please upgrade to the latest version. Learn more: https://aka.ms/gca | Upgrade your Graph connector Agent version by downloading the latest version from https://aka.ms/GCAdownload
1026 | Connection has failed due to a critical issue with the associated graph connector agent. Upgrade to the latest version or contact support to resolve the issue. Learn more: https://aka.ms/gca | Upgrade your Graph connector Agent version by downloading the latest version from https://aka.ms/GCAdownload
2001 | Indexing is throttled because of a large number of updates in the queue. Depending on the queue, it can take some time for the updates to complete. | Wait until the queue gets cleared.
2002 | Indexing failed due to unsupported item formatting. | For more information, see connector-specific documentation.
2003 | Indexing failed due to unsupported item content. | For more information, see connector-specific documentation.
2004 | Indexing failed due to unsupported item or file size. | For more information, see connector-specific documentation.
2005 | Indexing failed because the URI is too long. | For more information, see connector-specific documentation.
2006 | User mapping failed due to an invalid mapping formula or no Azure AD user with this property. | Try deleting and recreating the connection with a different mapping formula. 
2007 | This item won't be displayed in Microsoft Search because some users or groups without permission to view this item couldn't be indexed. | 
2008 | Connections can't have non-Azure AD groups with more than 50,000 members. | Try removing users from a group or try removing items ACLed with that group from ingestion and recreate the connection.
2009 | Non-Azure AD group indexing is temporarily paused due to a large number of requests. Indexing will resume when the system finishes processing these requests. Check back later. | 
2010 | This connection is no longer valid because of an update made by Microsoft. | Delete the connection and create a new one.
5000 | Something went wrong. If this issue continues, contact support. |
