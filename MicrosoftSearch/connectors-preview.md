---
title: "Connectors preview"
ms.author: v-pamcn
author: TrishaMc1
manager: mnirkhe
ms.date: 10/08/2019
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Priority
search.appverid:
- BFB160
- MET150
- MOE150
description: "Microsoft Graph Connectors preview."
---

# Microsoft Graph connectors Preview
Microsoft Graph connectors, indexing APIs, and search APIs are currently in preview. We encourage customers to try the connectors and provide feedback. We don’t encourage customers to deploy connectors in production during the preview period.

## Set up targeted release
To try connectors, you must have the Targeted release option set for your tenant. The Targeted release requirement applies no matter which of the following preview environments you choose.
To learn more about the Targeted release option and how to set it, see [Set up the Standard or Targeted release options in Office 365](https://docs.microsoft.com/en-us/office365/admin/manage/release-options-in-office-365?view=o365-worldwide).

## Choose a preview environment 
To try connectors, indexing APIs, and search APIs, we recommend these two methods:
1.	**Test tenant**.  We encourage you to use a test tenant to try the Microsoft Graph connectors preview.
2. **Test site collection**. If you don’t have a test tenant, you can create a site collection to try out connectors functionality. To show results from connectors without impacting the search pages anywhere else in your tenant, customize the search experience of only that site collection.

## Preview limitations
The Preview release includes these limitations:
* Ingestion throughput is throttled at about four items per second.
* There’s no support for schema updates. After you create a connection setup, there’s no way to update the schema. You can only delete and re-create the connection.
* Indexed content only shows up in the search results page under a custom vertical. This restriction applies to content with custom types.
* Before general availability, any connection you set up during Preview may need to be deleted and re-created. Those connections won’t work anymore if they’re incompatible with changes made to improve the product.
* Connections limit. Each tenant can create up to 10 connections only. 

To join the Preview program, sign up with the [Microsoft Graph Connectors Public Preview Interest Form](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbRxWYgu82J_RFnMMATAS6_chUNVYwNU1CMDNZUDBSSDZKWVo2RDJDRjRLQi4u).
