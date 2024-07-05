---
title: "Manage Power BI Search results"
ms.author: bstucker
author: bstuck
manager: bstucker
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
ms.assetid: c0c814d0-f7e4-444e-b18e-09beb45c9322
description: "Manage how Power BI reports and data appear in search results"
ms.date: 06/17/2024
---

# Manage Power BI search results

Users need to find data and analytics so that they can take informed decisions. To make it easier for users, Microsoft Search has added support to search for Power BI dashboards and reports. A few benefits of Power BI search are

* **Easy to use** This out-of-box search experience helps users find Power BI dashboards and reports easily across your organization.
* **Richer content** To make Power BI search results more useful, they include key information like the type of content (dashboard or report) and the team or person who owns it.
* **Unified search experience** To maintain a cohesive experience, Power BI results are consistent across all search entry points. Wherever you search, you'll get the same results with the same look and feel.

## What users experience

Microsoft Search users can search for Power BI results from the Windows search box, SharePoint, Microsoft 365, and Bing. 

Power BI results can be queried from All tab on the Search page

![PowerBI All Tab](https://github.com/MicrosoftDocs/OfficeDocs-MicrosoftSearch-pr/assets/72018014/70c6d1c8-5863-4518-b0b6-10da777ec96e)

Power BI results can also be queried from the dedicated Power BI Custom vertical

![PowerBI-Vertical](https://github.com/MicrosoftDocs/OfficeDocs-MicrosoftSearch-pr/assets/72018014/1a0bc8ac-0c8e-42f7-b4e7-8ff41539774c)

## Manage Power BI search 

Power BI results are enabled by default. Your Power BI admin can manage them at any time. To manage in the Power BI Admin portal, go to settings and toggle the **Share data with your Microsoft 365 Services** setting. To learn more, see [Administering Power BI in the admin portal](/power-bi/admin/service-admin-portal#use-global-search-for-power-bi-preview).

![PowerBI Admin - Search settings](https://github.com/MicrosoftDocs/OfficeDocs-MicrosoftSearch-pr/assets/72018014/c3641943-85d4-43b7-8952-613ebe6868de)

Power BI search vertical is enabled by default in the list of verticals. It can be disabled from the Verticals page if required.

![PowerBI vertical with disable option](https://github.com/MicrosoftDocs/OfficeDocs-MicrosoftSearch-pr/assets/72018014/1a6d05a3-69ed-4ab4-b662-2c4ed0516675)

> [!NOTE]
> When using Microsoft Search, your search query and the results returned from Power BI, could be processed in a region or geography different than where your Power BI data is located.

## Limitations

* Power BI inline results experience isn't available in SharePoint site search scope.
* All vertical configurations don't apply to Power BI content. Example: The All-tab keyword query language filter (KQL) "FileType:xlsx" can be used to filter out Excel files from SharePoint and OneDrive, but will not prevent Power BI content from showing.
* All vertical sorting by date don't apply to Power BI results. Sorting by date instead of relevance will exclude Power BI results.

## Frequently Asked Questions

**Q: Is Power BI search enabled by default?**

**A:** Yes. Power BI search is enabled by default for Microsoft Search. 

**Q: Can Power BI search be enabled or disabled for specific groups or users?**

**A:** No. It can only be enabled or disabled for your entire organization.

**Q: Can I customize the Power BI search results (for example, the report type or report owner)?**

**A:** No. We don’t support customizing the fields included in Power BI search results.

**Q: How much time does it take to see the affect of Power BI Admin toggle in Microsoft Search?**

**A:** It generally reflects in a few hours. In some cases it may take upto a day to show up in the list of Verticals.
