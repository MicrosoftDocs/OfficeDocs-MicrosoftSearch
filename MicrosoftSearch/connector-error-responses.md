ms.date: 10/02/2019
title: " Error responses in Microsoft Graph connectors"
ms.author: danielabom
audience: Admin
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
description: "Learn how to identify and handle error responses in Microsoft Graph connectors."
---
# Error responses in Microsoft Graph connectors

Download error report is available in the errors tab of the connection pane. A limited number of connection errors are shown in the UI of the connection pane. To get the complete list of errors, you can run the PowerShell script to download the complete error report. Here are the steps to generate the report:

* Open Windows PowerShell with administrator rights.
* Run the command to download and install the script from the PowerShell Library.

```powershell
    Install-Script -Name DownloadErrorScript
```

* This script downloads the item errors in a Microsoft Graph connectors connection. An Msal token is generated using the tenant credentials in which the connection is present. The token is generated using MSAL.PS module, while installing this PS script, MSAL.PS module should be installed automatically. If this doesn't happen use the below command to install MSAL.PS

```powershell
    Install-Module -Name MSAL.PS
```

* To know more about the script refer [DownloadErrorScript](https://www.powershellgallery.com/packages/DownloadErrorScript/2.1)
* Once the install is complete run:

```powershell
    DownloadErrorScript.ps1
```

* Provide the connectionId of the connection for which you want to download the error report.
* Give the name of the output file without extension as by default .csv extension is used.
* Give the batch limit of the download. This is an optional parameter. A batch limit defines the batch of errors that is fetched from the service. Each batch fetch takes a few seconds. If you have a large number of errors in the order of thousands, larger batch size can be used to reduce the time spent in fetching the data with each batch. However, if the errors are in the order of hundreds, a low batch size would be ideal. Please note increasing batch size may increase the probability of failures. The maximum batch size limit is 5000.
* The script will ask you to log in from the tenant account. After the login is complete, the download will start.
* It will take some time based on the batch size and the number of errors to complete the download. The downloaded file will be present in the same path from where the script was run with the name given during the run.

:::image type="content" alt-text="Screenshot that shows PowerShell script run to download the error report." source="media/errorreport.png" lightbox="media/errorreport.png":::

## Monitor errors

For each **Active Connector** on the **Data sources** tab, any existing crawl errors show under the **Current crawl** header, in the **Errors** section. It lists error codes, the count of each, and error log download options. You can select an **error code** to view the error's details.

:::image type="content" source="media/errormonitoring1.png" alt-text="Screenshot that shows details pane showing the current crawl, and errors section for the selected connector.":::

To view an error's specific details, select its error code. A screen appears with error details and a link. The most recent errors appear at the top.

The following list shows the different errors that can appear against any connection.

Error code | Error message | Solution
--- | --- | ---
1000 | The data source isn't available. Check your internet connection or make sure the data source is still accessible by the connector. | This error occurs when the data source isn't reachable due to a network issue or when the data source itself is deleted, moved, or renamed. Check if the data source details provided are still valid.|
1001 | Can't update the data because the data source is throttling the connector. | To unthrottle the data source, check if its scale limits can be increased or wait until a less traffic-heavy time of the day.|
1002 | Can't authenticate with the data source. Verify that the credentials associated with this data source are correct.| Select **Edit** to update the authentication credentials.|
1003 | The account associated with the connector doesn't have permission to access the item. |Ensure the proper account has access to the item you want indexed.|
1005 | Credentials associated with this data source have expired. Renew the credentials and update the connection.| Select **Edit** to update the authentication credentials.|
1008 | The total quota utilization of your tenant has reached its limit. | Try deleting a connection to free up some of your quota or adjusting your ingestion filters to bring in less data. If these steps don't solve the issue, contact Microsoft support.|
1009 | The total quota utilization for your connection has reached its limit. | Try adjusting your ingestion filters to bring in less data. If this step doesn't solve the issue, contact Microsoft support.|
1010 | The total quota utilization for indexing non-Azure AD groups has reached its limit of 100 K. | Try deleting a connection to free up some of your quota or adjusting your ingestion filters to bring in less data. If these steps don't solve the issue, contact Microsoft support.
1011 | The Microsoft [Graph connector agent](graph-connector-agent.md) isn't reachable or offline. |
1012 | Authentication to your connection failed due to an unsupported authentication mode. | Edit the connection to update the authentication settings for your connection.|
1015 | Connections created on this agent will fail due to insufficient permissions. Grant the ExternalItem.ReadWrite.OwnedBy  permission to the Microsoft Azure app used for registration to allow the app to read and write all external items without a signed-in user and resume the crawl. | Ensure that the Azure app used for Agent registration has ExternalItem.ReadWrite.OwnedBy  permission.|
1016 | Connections created on this agent will fail due to insufficient permissions. Grant the Directory.Read.All  permission to the Microsoft Azure app used for registration to read data in your organization's directory and resume the crawl. | Ensure that the Azure app used for Agent registration has a Directory.Read.All permission.|
1017 | Item can't be indexed because the network is unavailable. | Restore the network and wait for the next crawl for the item to get indexed.|
1018 | Please ensure that the entered user account has interactive logon rights to the machine where the Microsoft Graph connector agent is installed. | Ensure that the user account has interactive logon rights to the machine where the Microsoft Graph connector agent is installed. Refer to the [documentation](graph-connector-agent.md#connection-failure) to learn more.|
1019 | Connection failed because the app credentials given to GCA instance are invalid or expired. Please update the credentials. | Check your app credentials for GCA instance associated with the connection.|
1020 | The Microsoft Graph connector agent associated with the connection is not able to connect to GRPC connector server. | The GCA instance could not crawl the data source as there was an issue with connecting to the custom connector over GRPC.|
1025 | The Microsoft Graph Connector Agent associated with this connection is deprecated due to critical issues, please upgrade to the latest version. Learn more: https://aka.ms/gca | Upgrade your Microsoft Graph connector agent version by downloading the latest version from https://aka.ms/GCAdownload|
1026 | Connection has failed due to a critical issue with the associated Microsoft Graph connector agent. Upgrade to the latest version or contact support to resolve the issue. Learn more: https://aka.ms/gca | Upgrade your Microsoft Graph connector agent version by downloading the latest version from https://aka.ms/GCAdownload|
2001 | Indexing is throttled because of a large number of updates in the queue. Depending on the queue, it can take some time for the updates to complete. | Wait until the queue gets cleared.|
2002 | Indexing failed due to unsupported item formatting. | For more information, see connector-specific documentation.|
2003 | Indexing failed due to unsupported item content. | For more information, see connector-specific documentation.|
2004 | Indexing failed due to unsupported item or file size. | For more information, see connector-specific documentation.|
2005 | Indexing failed because the URI is too long. | For more information, see connector-specific documentation.|
2006 | User mapping failed due to an invalid mapping formula or no Microsoft Entra user with this property. | Try deleting and recreating the connection with a different mapping formula.
2007 | This item won't be displayed in Microsoft Search because some users or groups without permission to view this item couldn't be indexed. |
2008 | Connections can't have non-Azure AD groups with more than 50,000 members. | Try removing users from a group or try removing items ACLed with that group from ingestion and recreate the connection.|
2009 | Non-Azure AD group indexing is temporarily paused due to a large number of requests. Indexing will resume when the system finishes processing these requests. Check back later. |
2010 | This connection is no longer valid because of an update made by Microsoft. | Delete the connection and create a new one.|
5000 | Something went wrong. If this issue continues, contact support.|
