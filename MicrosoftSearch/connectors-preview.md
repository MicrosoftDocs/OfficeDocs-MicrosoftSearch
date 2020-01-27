---
title: "Connectors preview"
ms.author: mounika.narayanan
author: monaray
manager: shohara
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Find out about Microsoft Graph Connectors preview for Microsoft Search."
---

# Microsoft Graph connectors preview

Microsoft Graph connectors and Microsoft Search APIs (query and index) are currently in preview status. To gain access to connectors functionality, you must request to join the preview program by submitting the <a href="https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbRxWYgu82J_RFnMMATAS6_chUNVYwNU1CMDNZUDBSSDZKWVo2RDJDRjRLQi4u" target="_blank">Microsoft Graph Connectors Preview Sign up Form</a>. This is an early preview, and there's no service level guarantee. We encourage customers to try connectors functionality and provide feedback. We don’t recommend using connectors for production purposes during the preview period.

## Set up Targeted release
To try connectors, you must have the **Targeted release** option set for all users in your organization. The Targeted release requirement applies no matter which of the following preview environments you choose.
To learn more about the Targeted release option and how to set it, see <a href="https://docs.microsoft.com/office365/admin/manage/release-options-in-office-365?view=o365-worldwide" target="_blank">Set up the Standard or Targeted release options in Office 365</a>.

## Choose a preview environment 
To try connectors, indexing APIs, and search APIs, we recommend these two methods:
1. **Test tenant**.  We encourage you to use a test tenant to try the Microsoft Graph connectors preview.
2. **Test site collection**. If you don't have a test tenant, you can create a test site collection to try out connectors functionality. To show results from connectors without impacting the search pages anywhere else in your organization, customize the search experience of only that site collection.

## Preview limitations
The preview release has the following limitations: 
* Ingestion throughput is throttled at about four items per second.
* There's no support for schema updates. After you create a connection setup, there's no way to update the schema. You can only delete and re-create the connection.
* Indexed content only shows up in the search results page under a custom vertical. This restriction applies to content with custom types.
* Before general availability, any connection you set up during the preview period might need to be deleted and re-created. Those connections won't work anymore if they're incompatible with changes made to improve the product.
* There's a connections limit. Each tenant can create up to 10 connections.
