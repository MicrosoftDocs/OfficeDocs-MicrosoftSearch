---
title: "Connectors Result Cluster Experience"
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

ROBOTS: NOINDEX, NOFOLLOW
---
# Connectors Result Cluster Experience 

## Overview of the Connectors result cluster (Preview)  
 With Connectors result clusters, enterprises can search for content from third party data sources in their default view (the All tab) in SharePoint, Office.com and Microsoft Search in Bing. 

Result clusters help users easily discover and explore third party content previously only in search verticals tied to connectors. The results shown in a result cluster are grouped together based on how they are configured by the tenant administrator in a search vertical.  

## How connector results are selected  
Connector results provided in the result cluster are derived from individual search verticals with connector content. Each search vertical provides a set of relevant results which becomes a candidate result cluster. Relevant results are chosen based on the "title" property, result snippet, and content component of each item. 

To ensure discovery of content from the search verticals, we recommend providing meaningful titles for your items. This positively impacts the arbitration of result cluster candidates and the likelihood of your content showing up in a result cluster. For example, avoid the use of IDs as values for the property "title" unless your users are using IDs to look for content. 

How often a result cluster is shown varies on factors such as the number of search verticals that you configure and the type of content. By either selecting or ignoring result cluster results, you will implicitly provide hints that will adjust the triggering of result clusters over time.

## Search result experience for connector results
The search result experience for connector items shown in your result cluster is system generated. You must declare the "title" property and item content during connection registration if you want results to appear in your result cluster. The result cluster does not use result layout defined using result type.

## Preview limitations  
If you have tried using the result cluster experience in the preview phase, please let us know which aspects work well and which need improvement.

## Enabling this experience   
The result cluster experience is turned off by default.  
Follow these steps to turn on the experience at the organization level:   

Microsoft 365 Admin Center
1.	In the [Microsoft 365 admin center](https://admin.microsoft.com/), go to **Settings** > **Microsoft Search** > **Customization** > **Verticals**.  
2.	Select  the **All** vertical and go to the **Show connector results** section. Turn on the experience at the site level. 

Sharepoint
1. On the SharePoint site where you want the result cluster experience, go to **Settings**. 
2. 	Go to **Site information**>**View all site settings**. 
3.	Go to the Microsoft Search section, then select **Configure Microsoft Search for this site collection**.
4.	In the navigation pane, go to **Custom experience**, then select **Verticals**. 
5.	Select the **All** vertical, then enable **Show connector results**.

## View the result cluster experience after it is enabled
After you turn on the result cluster experience, it might take a while before you can view it. If you want the experience immediately, you can append *cacheClear=true* to the URL in SharePoint and Office.  

