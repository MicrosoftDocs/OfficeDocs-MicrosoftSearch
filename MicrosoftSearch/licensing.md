---
ms.date: 11/02/2020
title: "Index quota"
ms.author: mecampos
author: mecampos
manager: umas
audience: Admin
ms.audience: Global or Billing Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
description: "Index quota of Microsoft Graph connectors for Microsoft Search and Microsoft 65 Copilot."
---
<!---Previous ms.author: rusamai --->

# Index quota

Any valid **Microsoft 365 Copilot, Microsoft 365 or Office 365 license** allows you to view data from connectors in your Microsoft 365 Copilot and Microsoft Serach results.

>[!IMPORTANT]
>All of the connectors by Microsoft are free. Microsoft provides an index quota limit of 50 million items per tenant without any extra cost.

## Index quota items

An item represents one unit of index quota. Each entity (or record) from the source system that is added to Microsoft Graph is considered an item. In Microsoft Graph, each item appears as a unique citation in Microsoft 365 Copilot responses and as a distinct search result in Microsoft Search. 

Depending on the type of data source, an item is defined as – 
-	1 document (Word, Excel, PPT, PDF, etc.) in a file share
-	1 wiki page in Confluence
-	1 webpage on a website
-	1 ticket/issue in Jira

Total quota utilized is calculated in terms of total items stored in the index. The number of updates/changes to an item are not counted in any manner.

## Purchase of add-on index quota
To purchase more Microsoft Graph connectors quota, contact your Microsoft account manager or complete the following steps:

The Microsoft 365 admin center currently has two layouts to navigate to purchase services.

1. Go to **[Microsoft 365 admin center](https://admin.microsoft.com)**

If, on the left-hand side you see **Marketplace**:
1. Go to **Marketplace**
2. Select **All products** at the top of the Marketplace page.
3. Search for **Extra Graph Connector Capacity** in the search at the top of the Marketplace page.
4. Select the **Details** button for **Extra Graph Connector Capacity**.

If, on the left hand side you see **Billing**:
1. go to **Billing > Purchase services**.
2. At the bottom of the Purchase services page, select **Add-ons**.
3. Select **Extra Graph Connector Capacity**.

Finally:
1. Select **Buy**, and then complete your order preferences.
2. Select **Check out now**.

Cost of indexing connector content is $1000/month for every million items. This is assessed for items exceeding the entitled quota for each tenant (refer next section).

### Index quota for enterprise users

All qualified* enterprise customers get a 50M entitlement. 

The following licenses include entitlement to 50 million items of index quota, which counts towards your organization's quota for ingesting content from Microsoft Graph connectors.

|License name|
|:--- |
|Microsoft 365 Copilot|
|Microsoft 365 E5 or Office 365 E5|
|Office 365 E1|
|Office 365 E3|
|Office 365 E5|
|Microsoft 365 E3|
|Microsoft 365 E5|
|Microsoft 365 F1|
|Microsoft 365 F3|
|Office 365 F3|
|Microsoft 365 Business Basic|
|Microsoft 365 Business Standard|
|Microsoft 365 Business Premium|
|Office 365 G1|
|Office 365 G3|
|Office 365 G5|
|Microsoft 365 G3|
|Microsoft 365 G5|
|Office 365 A3|
|Office 365 A5|
|Microsoft 365 A3|
|Microsoft 365 A5|  

For example, if your organization has 100 Microsoft 365 E5 licenses, then your organization has 100 x 500 = 50,000 items worth of Microsoft Graph connectors index quota.

> [!NOTE]
> * Microsoft 365 A5 and Office 365 A5 do not include this entitlement.
> * Microsoft 365 Copilot, Microsoft 365 E5 or Office 365 E5 license is not required for using Microsoft Graph connectors.
> [!NOTE]
> By default, Microsoft Graph connectors support up to 50 million items of total index quota, which includes any built-in quota bundled into Microsoft 365 Copilot, Microsoft 365 or Office 365 E5 licenses. The per connection item limit is 5 million items by default. If you need higher item count per connection please reach out to your Microsoft account manager or fill up this [form](https://aka.ms/GraphConnectorsHigherCapacity).
>
> Preview connectors do not count against quota; after a connector becomes generally available, it starts to count on the total index quota.

