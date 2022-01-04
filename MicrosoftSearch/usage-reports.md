---
title: "Search Usage Reports"
ms.author: ankmis
author: jeffkizn
manager: parulm
ms.topic: article
ms.service: mssearch
audience: Admin
ms.audience: Admin
ms.date: 01/04/2022
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
description: "Review Microsoft Search usage reports"
---

# Microsoft Search Usage Reports

Search usage reports enable you to gain more understanding of how search is functioning in your organization. The insights generated from these reports will help you take actions that will make search a more useful and delightful experience for your users.

The [Microsoft Search usage reports](https://admin.microsoft.com/Adminportal/Home?#/MicrosoftSearch/insights) include graphs and tables generated from searches that are executed from SharePoint Home (the site with URL ending in /SharePoint.aspx), Office.com, and Microsoft Search in Bing work tab search boxes. You can see data from the past 7 days, 14 days, 31 days, or monthly for the previous year.

:::image type="content" source="media/usage-reports/usage_reports_v3.png" alt-text="A report dashboard that shows graphs and tables of search usage." lightbox="media/usage-reports/usage_reports_v3.png":::

## Overview of search reports

| Report | Description |
|:-----|:-----|
|Query Volume|This report shows the number of search queries performed. Use this report to identify search query volume trends and to determine periods of high and low search activity.|
|Top Queries|This report shows the most popular search queries. A query is added to this report when it is searched at least three times with a click on a result. Use this report to understand what types of information your users are searching for.|
|Abandoned Queries|This report shows popular search queries that receive low click-through. Use this report to identify search queries that might create user dissatisfaction and to improve the discoverability of content. You can then determine if creating an answer, like a Bookmark, or ingesting new content through a Graph connector is the right action.|
|No Results Queries|This report shows popular search queries that returned no results. Use this report to identify search queries that might create user dissatisfaction and to improve the discoverability of content. You can then determine if creating an answer, like a Bookmark, or ingesting new content through a Graph connector is the right action.|

>[!NOTE]
>There is currently a known issue where queries satisfied by an answer like a Bookmark are counted as an abandoned query.

## Viewing reports

When you navigate to the usage reports page, all the reports are available to view. You can use the date filter to pick a specific day or month to view.

Downloading a report will allow you to see reports from a broader range of time. The report downloads as an Excel spreadsheet based on the selected date filter. If you chose past 7, 14, or 31 days, the spreadsheet will have an individual tab for each day. The past 12 months download will have a tab for each month.
