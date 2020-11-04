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
Graph connectors are a great way for enterprises to onboard and search for new content sources that are not part of Microsoft 365. With Connectors Result Clusters, enterprises can now search for content from third party data sources in their default view (the All tab) in SharePoint, Office.com and Microsoft Search in Bing. 

Result clusters help users easily discover and explore third party content which was previously only present in search verticals tied to connectors. The results shown in a result cluster are grouped together based on how they are configured by the tenant administrator in a search vertical.  

## How connector results are selected  
Connector results provided in the Result Cluster are derived from individual search verticals with connector content. Each search vertical provides a set of relevant results (currently the top two) which becomes a Result Cluster candidate. Candidates are chosen based on relevant clues derived from the ‘title’ and ‘result snippet’ properties of the results and the content part of the items. 

To ensure discovery of content from the search verticals, we highly recommend providing meaningful and informative titles for your items. This positively impacts the arbitration of candidates, and the likelihood of your content to show up in a Result Cluster. Avoid the use of IDs as ‘title’ – unless your users are using IDs to look for content. 

How often a Result Cluster is shown varies on several factors such as the number of search verticals that you configure and the type of content. By interacting with Result Clusters, either by clicking on them or ignoring them, you will implicitly provide hints that over time will adjust the triggering of Result Clusters.

## Search result experience for connector results
The search result experience for connector items shown in Result cluster is system generated. You must declare the properties that are going to be used as ‘Title’ and ‘Content’ during connection registration for results to appear in Result Cluster. The result cluster does not use result layout defined using result type.

## Preview limitations  
Result Clusters is presently in preview as we are working to ensure that the experience doesn’t have any impact on performance and ensuring high quality of the connectors results shown.  

During the preview phase, we would love to get feedback from customers who have tried out the experience and let us know which aspects work well and which need improvement.

## Enabling this experience   
The Result Cluster experience is turned off by default.  
Turn on the experience at organization level:   
1.	In the Microsoft 365 admin center, go to Settings > Microsoft Search > Customization > Verticals.  
2.	Select  ‘All’ vertical to find ‘Show connector results’. 
Turn on the experience at the site level 
1.	On the SharePoint site where you want the experience, go to Settings. 
2.	Select Site information and then View all site settings. 
3.	Look for the Microsoft Search section, and then select Configure Microsoft Search for this site collection. 
4.	In the navigation pane, go to Custom experience, and then select the Verticals tab. 
5.	Select  and open ‘All’ vertical to find ‘Show connector results’.

## View the Result cluster experience after it's enabled
After you turn on the result cluster experience, it might take a while before you  can view it. If you don't want to wait after turning it on, you can append cacheClear=true to the URL in SharePoint and Office to try the experience immediately.  


