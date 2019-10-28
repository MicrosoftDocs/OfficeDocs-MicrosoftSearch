---
title: "Connectors preview"
ms.author: v-pamcn
author: TrishaMc1
manager: mnirkhe
ms.date: 10/08/2019
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Microsoft Graph Connectors preview."
---

# Microsoft Graph Connectors preview

Microsoft Graph connectors, indexing APIs and search APIs are currently in preview. We encourage customers try the connectors and provide us with feedback. We do not encourage customers to use connectors in production during the preview period. 
 
## Targeted Release Requirement 
To try connectors, you must have the Targeted release option set for either your tenant, or for your Search and Tenant admins. The Targeted release requirement applies regardless of which preview environment you choose below. 
 
To learn more about the Targeted Release option and how to set it, click [here](https://docs.microsoft.com/en-us/office365/admin/manage/release-options-in-office-365?view=o365-worldwide). 

## Environment for Preview 
There are 2 ways that we recommend customers to try out connectors, the indexing APIs and search APIs: 
1.	Test tenant. Many customers have a tenant that they use to try out new features before moving full-scale production. If your organization has a test tenant, we encourage you to use it to try connectors and give us feedback. 
2.	Site collection. If you don’t have a test tenant, you can create a site collection specifically to try out connector functionality. You can customize the search experience of only that site collection to show results from connectors without impacting the search pages elsewhere in your tenant. 
 
## Preview limitations 
During the Preview period, you should expect the following: 
* Any connection that has been set up may need to be deleted and re-created due to incompatible changes made to improve the product. 
* Throttled ingestion throughput. Ingestion throughput is throttled at about 4 items per second. 
* No support for schema updates. Once a connection setup is complete, there is no way to update the schema. You will need to delete and re-create the connection. 
* Except for content ingested as a file, the content will only show up in the search results page under a custom vertical. This applies mainly to content where user-defined-types are used. 

 
To join the preview program, click [here](https://forms.office.com/Pages/DesignPage.aspx#FormId=v4j5cvGGr0GRqy180BHbRxWYgu82J_RFnMMATAS6_chUNVYwNU1CMDNZUDBSSDZKWVo2RDJDRjRLQi4u&Preview=%7B%22PreviousTopView%22%3A%22None%22%7D&TopView=Preview).



