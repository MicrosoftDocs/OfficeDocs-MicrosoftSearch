---
ms.date: 11/02/2020
title: "Index quota for Microsoft Graph connectors"
author: danielabom
ms.author: danielabo
manager: stevewilkins
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
description: "Index quota for Microsoft Graph connectors."
---
# Index quota
Any valid Microsoft 365 Copilot, Microsoft 365, or Office 365 license allows you to view data from connectors in your Microsoft 365 Copilot and Microsoft Search results.

>[!IMPORTANT]
>All Microsoft connectors are provided at no additional cost. Microsoft offers an index quota limit of 50 million items per tenant, included at no extra charge. For more information, see this [public announcement](https://techcommunity.microsoft.com/t5/copilot-for-microsoft-365/bg-p/Microsoft365CopilotBlog).

## What represents items in an index quota?
An item represents one unit of index quota. Each entity (or record) from the source system that is added to Microsoft Graph is considered an item. In Microsoft Graph, each item appears as a unique citation in Microsoft 365 Copilot responses and as a distinct search result in Microsoft Search. 

Depending on the type of data source, an item is defined as– 
-	1 document (Word, Excel, PPT, PDF, etc.) in a file share
-	1 wiki page in Confluence
-	1 webpage on a website
-	1 ticket or issue in Jira

The total quota utilized is based on the number of items stored in the index. The frequency of updates or changes to an item does not affect the quota calculation.

### Index quota for Microsoft 365 enterprise users

All eligible Microsoft 365 enterprise customers with one of the following licenses are entitled to 50 million items of index quota. This quota contributes to your organization’s allocation for ingesting content through Microsoft Graph connectors. For example, if your organization holds 100 Microsoft 365 E5 licenses, it is allocated a Microsoft Graph connectors index quota of 100 x 500 = 50,000 items.

|License name|
|:---|
|Microsoft 365 Copilot|
|Microsoft 365 Business Basic|
|Microsoft 365 E5 or Office 365 E5|
|Microsoft 365 Business Standard|
|Office 365 E1|
|Microsoft 365 Business Premium|
|Office 365 E3|
|Office 365 G1|
|Office 365 E5
|Office 365 G3|
|Microsoft 365 E3|
|Office 365 G5|
|Microsoft 365 E5|
|Microsoft 365 G3|
|Microsoft 365 F1|
|Microsoft 365 G5|
|Microsoft 365 F3
|Office 365 A3|
|Office 365 F3|
|Office 365 A5|
|Microsoft 365 A3|
|Microsoft 365 A5|  

> [!NOTE]
>Microsoft Graph connectors support up to 50 million items of total index quota at no additional cost. By default, the item limit per connection is 5 million items. If you require a higher item count per connection or wish to increase your overall index quota, please contact your Microsoft account manager or complete this [form](https://aka.ms/GraphConnectorsHigherCapacity).
> 
>Preview connectors do not count against the quota. Once a connector transitions to general availability, it starts counting toward the total index quota.
