---
ms.date: 11/02/2020
title: "Microsoft Graph connectors license requirements and pricing"
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
description: "License requirements and pricing for Microsoft Graph connectors for Microsoft Search."
---
<!---Previous ms.author: rusamai --->

# License requirements and pricing

This article is for global or billing admins who want to learn about how to purchase more Microsoft Graph connectors quota for their organization.

Any valid **Microsoft 365 Copilot, Microsoft 365 or Office 365 license** allows you to view data from connectors in your search results.

>[!IMPORTANT]
>All of the connectors by Microsoft are free. However, you need to have sufficient index quota to ingest content from those connectors.

To index content by using Microsoft Graph connectors, you need to have sufficient index quota. Microsoft Graph connectors index quota is available via:

- Purchase of add-on index quota
- Built-in entitlements

## What is an item of index quota?
An item is 1 unit of index quota.  Each entity (or record) from the source system that you add to Microsoft Graph can be considered an item. Each item added to Microsoft Graph shows up as a unique citation in a Copilot response and as a unique search result in Microsoft Search. Depending on the type of data source, 1 item is – 
-	1 document (word, excel, ppt, pdf, etc.) in file share
-	1 wiki page in Confluence
-	1 webpage in a website
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

## Entitlement built into Microsoft 365 Copilot, Microsoft 365 & Office 365 E5 licenses

The following licenses include entitlement to 500 items of index quota, which counts towards your organization's quota for ingesting content from Microsoft Graph connectors:

* Microsoft 365 Copilot
* The Microsoft 365 E5 or Office 365 E5

For example, if your organization has 100 Microsoft 365 E5 licenses, then your organization has 100 x 500 = 50,000 items worth of Microsoft Graph connectors index quota.

<!---Comment requested in PR#143--->
> [!NOTE]
> * Microsoft 365 A5 and Office 365 A5 do not include this entitlement.
> * Microsoft 365 Copilot, Microsoft 365 E5 or Office 365 E5 license is not required for using Microsoft Graph connectors.
> [!NOTE]
> By default, Microsoft Graph connectors support up to 50 million items of total index quota, which includes any built-in quota bundled into Microsoft 365 Copilot, Microsoft 365 or Office 365 E5 licenses. The per connection item limit is 5 million items by default. If you need higher item count per connection please reach out to your Microsoft account manager or fill up this [form](https://aka.ms/GraphConnectorsHigherCapacity).
>
> Preview connectors do not count against quota; after a connector becomes generally available, it starts to count on the total index quota.

