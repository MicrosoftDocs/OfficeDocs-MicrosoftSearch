---
title: "Connectors result cluster"
ms.author: manusi
author: manusi
manager: ruppala
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Details of the Connectors Result Cluster experience"
---
# Graph connectors result cluster

## Overview of the Graph connectors result cluster (Preview)  

With Graph connectors result clusters, enterprises can search for content from third party data sources in their default view (the All tab) in SharePoint and Office.com.

Result clusters help users discover all third party content (previoulsy tied to a single connector and vertical) in one place. The results shown in a result cluster are grouped together based on how the tenant administrator configures them in a search vertical.  

## How connector results are selected and displayed

Connector results provided in the result cluster are derived from individual search verticals with connector content. Each search vertical provides a set of relevant results which becomes a candidate result cluster. Relevant results are chosen based on the "title" property, result snippet, and content component of each item.

To ensure discovery of content from the search verticals, we recommend providing meaningful titles for your items. This positively impacts the arbitration of result cluster candidates and the likelihood of your content showing up in a result cluster. For example, avoid the use of IDs as values for the property "title" unless your users are using IDs to look for content.

How often a result cluster is shown varies on factors such as the number of search verticals that you configure and the type of content. By either selecting or ignoring result cluster results, you will implicitly provide hints that will adjust the triggering of result clusters over time.

The search result experience for connector items shown in your result cluster is system generated and does not use custom result layouts. You must declare the "title" property and item content during connection registration if you want results to appear in your result cluster.

## Enable result clusters
  
The result cluster experience is turned off by default.  

Follow these steps to turn on the experience at the organization level:

1. In the [Microsoft 365 admin center](https://admin.microsoft.com/), go to **Settings** > **Search & intelligence** > **Customization** > **Verticals**.  
2. Select  the **All** vertical, then enable **Show connector results**. 


Follow these steps to turn on the experience at the site level:

1. On the SharePoint site where you want the result cluster experience, go to **Settings**.
2. Go to **Site information**>**View all site settings**.
3. Go to the Microsoft Search section, then select **Configure Microsoft Search for this site collection**.
4. In the navigation pane, go to **Custom experience**, then select **Verticals**.
5. Select the **All** vertical, then enable **Show connector results**.

## View the result cluster experience after it is enabled

After you turn on the result cluster experience, it might take a few minutes before you can view it. If you want the experience immediately, you can append *cacheClear=true* to the URL in SharePoint and Office.
