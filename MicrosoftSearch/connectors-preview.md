---
title: "Connectors preview"
ms.author: monaray
author: monaray97
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

Microsoft Graph connectors and Microsoft Search APIs (query and index) are currently in preview status. To gain access to connectors functionality, you must turn on the Targeted release option in your tenant. This is an early preview, and there's no service level guarantee. We encourage customers to try connectors functionality and provide feedback. We don’t recommend using connectors for production purposes during the preview period.

## Set up Targeted release

To try connectors, you must have the **Targeted release** option set for all users in your organization. To learn more about the Targeted release option and how to set it, see [Set up the Standard or Targeted release options in Office 365](https://docs.microsoft.com/office365/admin/manage/release-options-in-office-365?view=o365-worldwide).

## Choose a preview environment

To try connectors, indexing APIs, and search APIs, we recommend these two methods:

1. **Test tenant**.  We encourage you to use a test tenant to try the Microsoft Graph connectors preview.

2. **Test site collection**. If you don't have a test tenant, you can create a test site collection to try out connectors functionality. To show results from connectors without impacting the search pages anywhere else in your organization, customize the search experience of only that site collection.

## Preview limitations

The preview release has the following limitations:

* Ingestion throughput is throttled at about four items per second.

* There's no support for schema updates. After you create a connection setup, there's no way to update the schema. You can only delete and re-create the connection.

* Indexed content only shows up in the search results page under a custom vertical. This restriction applies to content with custom types.

* Any connection you set up during the preview period might need to be deleted and re-created. Those connections won't work anymore if they're incompatible with changes made to improve the product.

* There's a connections limit. Each tenant can create up to 10 connections.

* Source repository size. We recommend that you preview connectors with a source repository of about 200,000 items as this is our tested search scale limit. We are working on improving the performance of search, and we expect to support for larger repository sizes in the near future.

* Edit support for connection is not available. Once the connection has been created, you cannot edit or change it. If you need to change any details, you must delete and recreate the connection.

* Connector content can only be searched on custom verticals.

* Connector content from only one connection can be displayed in each custom vertical and requires result type creation.
