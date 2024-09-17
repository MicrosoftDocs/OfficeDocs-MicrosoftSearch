---
ms.date: 10/08/2019
title: "View your connection details"
ms.author: danielabo
author: danielabom
manager: SteveWilkins1123
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
description: "Access and manage your Microsoft Graph connectors as a search administrator for your tenant."
---
<!-- markdownlint-disable no-inline-html -->

# View your connection details

To access and manage your Microsoft Graph connectors, you must be designated as a search administrator for your tenant. Contact your tenant administrator to provision your account for the search administrator role.

To see your connections in the [Microsoft 365 admin center](https://admin.microsoft.com), go to the [Data sources tab](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/connectors).

You can view the connection details and errors by selecting the connection.  

:::image type="content" source="media/datasourcestab.png" alt-text="Screenshot that shows connectors list with a connector selected and details pane showing information about this connector.":::

## View Connection statistics 

Connection statistics help you get overall information on what is happening to the data after the first full crawl is completed successfully.

This section includes the data about the total number of items discovered, successfully indexed, or failed across all crawls. The data updates after every crawl and provides a cumulative perspective on the sync between the data source and the Microsoft Graph Connector index. With this information, you can swiftly identify discrepancies and ensure that their connection is up to date. 
The key perspective at this point is to understand the sync between the data source and the index is at a cumulative level and not just the last crawl. 

An item is indexed with the following information - content, properties (default + custom), and access.
1. We consider an item as completely indexed when all 3 parts of the item are indexed successfully. 
2. We consider an item as partially indexed when some part of the data is indexed however some part is missing. The item is still searchable with the remaining properties. E.g. For an item we could index all the content but could not index some properties. 

How to read the data in connection statistics:
| Sr. No |Section | Meaning |
|:---|:--- |:---:|
|1. |**Total number of discovered items** |Total items discovered in Data source during crawling. This is the number of items that the admin credentials have access to against the data source.|
|2. |**Items currently in index**|All the items that could be indexed, partially or completely.|
|2.a	|**Completely indexed items**|Total items successfully indexed with complete information attached to it including content, access, and properties.|
|2.b	|**Partially indexed items**|Items which are partially indexed<br> a) Partially indexed with incomplete ACL<br> b) Partially indexed with incomplete Data<br> c) Partially indexed with incomplete Properties <br>.|
|2.c	|**Items in the index but out of sync**|All items that were not updated with the latest information from the data source. This is attempted again in the next crawl.|
|3. |**Items failed to index**|Items that were discovered but were not processed due to any error. Further details of each error can be seen on the errors tab.|

## View your last crawl info

After the first initial incremental or full crawl completes successfully, the last crawl data values are displayed under the last crawl header in the detail pane. If there was no last crawl that ran, you don't see any information under the last crawl header. This information about the last crawl helps you gain insights into how the crawl performed and allows you to take necessary steps wherever required.

The following last crawl values are available for each connection:

|Value|Description| 
|:--- |:---|
| Completed at| Date and time the last crawl was completed.| 
| Type| Incremental or full crawl.| 
| Duration| How much time the last crawl took to completed.| 
| Successes| Number of items that have been successfully ingested in the last crawl.| 
| Errors| Number of items that produced an error in the last crawl.| 
