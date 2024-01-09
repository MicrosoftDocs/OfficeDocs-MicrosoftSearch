---
title: "Search Usage Reports"
ms.author: efrene
author: efrene
manager: scotv
ms.topic: article
ms.service: mssearch
audience: Admin
ms.audience: Admin
ms.date: 11/20/2020 
ms.localizationpriority: medium
ms.collection:
- scotvorg
search.appverid:
- BFB160
- MET150
- MOE150
description: "Review Microsoft Search usage reports"
recommendations: false
---

# Microsoft Search Usage Reports

Search usage reports enable you to gain more understanding of how people in your organization are using Microsoft Search. The insights generated from these reports will help you take actions that will make search a more useful and delightful experience for all your users.

:::image type="content" source="media/usage-reports/usage reports-key-metrics.png" alt-text="A dashboard showing key metrics for search and intelligence." lightbox="media/usage-reports/usage reports-key-metrics.png":::

The [Microsoft Search usage reports](https://admin.microsoft.com/Adminportal/Home?#/MicrosoftSearch/insights) include graphs and tables generated from searches that are executed from the SharePoint Start Page, SharePoint Sites, Microsoft 365 app (formerly known as the Office app) at office.com, and Bing. User analytics is also available for Windows Search, Outlook, Teams, OneDrive and application search in Word, Excel and PowerPoint. You can see data from the last 28 days or for the previous year.

On some detail pages, you can filter reports by country, occupation, department, or division. To protect privacy, if any filters show data for five or less individuals, those results won't be included in the search usage reports. In addition, these filters can be toggled on or off for the entire organization on the Org settings page, in case your organization has specific privacy requirements.  

## Search Application Coverage

These are the search applications that are currently included in tenant level usage reports:

| Search application | Description |
|:-----|:-----|
|Microsoft Search for Bing |A Bing search where the user is authenticated with organization credentials and the user navigated to the work tab in Microsoft Search in Bing.      |
|Microsoft365.com |The Microsoft 365 App at microsoft365.com (formerly known as the Office app at office.com).  |
|SharePoint Sites |SharePoint Online, including both classic (enterprise/site/basic search center) and modern (hub, communication, and team) site searches. |
|SharePoint Start page |The site available when selecting SharePoint in the Microsoft 365 app launcher with the URL ending in /SharePoint.aspx. |
|Windows Search Work results |Queries from the search box in the Start menu or taskbar for users authenticated with organization credentials and which produced work results.   |
|Outlook |Queries from Outlook for any device and platform. |
|Teams |Queries from Teams for any device and platform. |
|OneDrive |Queries in the OneDrive app that are used to search a user’s OneDrive for work or school.  |
|Word, Excel, PowerPoint |Aggregate of all queries in Word, Excel and PowerPoint.    |

## How to get to the Microsoft Search usage reports?

1. In the Microsoft 365 admin center, select **Settings**, then select **Search and Intelligence**.  
2. On the **Search and Intelligence** page, select the **Insights** tab, and then select **Summary**.

The search usage reports are available to users with the **search admin**, **search editor**, **global reader** or **global administrator** roles.

## What reports are available to me?

The Microsoft Search Usage Reports page provides you with search data through the following four reports:

- **User Analytics** – This section shows how people in your organization use Microsoft Search and allows you to compare user engagement and adoption across the search applications and time periods. It also allows you to go to a user's details page to view and analyze the user's data in more detail.  
- **Query Analytics** – This section shows key query metrics and a trend graph of queries and click-through queries over time. It also provides a breakdown of the query activity by user action, country, occupation and department or division. It also allows you to go to a query details page to view and analyze the queries in more detail.

- **Connection Analytics** – This section provides an analysis of your connections. Review queries and clicks for search results from your connections. It also allows you to go to a connection analytics details page to view and analyze the connection data in more detail. 
- **Answer Analytics** - This section provides you with impressions and click data for your editorial Bookmarks, Acronyms and Q&A's. It also gives information on impressions and clicks for individual Bookmark, Acronym and Q&A items.

You can view more details about the [User analytics](users-search-reports.md), [Query analytics](queries-usage-reports.md), [Answer analytics](answer-analytics-usage-reports.md) and [Connection analytics](connection-analytics-reports.md) sections by selecting the links.

> [!NOTE]
> These search usage reports show collective search data based on search traffic from the search applications listed above. You can also view and analyze search usage reports for individual modern SharePoint sites through their respective site collection usage reports. For more information, see [View search usage reports in modern sites](/sharepoint/view-search-usage-reports-modern-sites).





## Filters

At the top of the User analytics chart, you can use the following metrics to filter your data. These filters will also apply to not only the User analytics chart, but also the other reports on the Microsoft Search usage summary page.

| Filter | Description |
|:-----|:-----|
|Date Range |The date range for the analytics shown on the page: Last 28 days and Last 12 months.  |
|Search application |The search application where the user has performed the queries: Microsoft Search for Bing, Windows Search Work results, Outlook, Teams, OneDrive, Word/Excel/PowerPoint, SharePoint start page, SharePoint sites, Microsoft365.com or all applications combined. |

### Accessing search data prior to the start of new generation reports

Processing of the new search usage reports varies for different tenants. If you select a date range prior to the date processing started, you'll see a message stating **Data not available for entire time period selected**. To view data prior to this date, you need to use the previous usage analytics reports.

:::image type="content" source="media/usage-reports/data-not-available.png" alt-text="Data not available message." lightbox="media/usage-reports/data-not-available.png":::

To view the previous search analytics reports, select the **New usage reports** toggle on the top right corner of the page. 

:::image type="content" source="media/usage-reports/new-usage-toggle.png" alt-text="A toggle button.":::

## You can download reports

Most reports and tables in the Microsoft Search Usage Reports page have a download option that allows you to download the background data for the report that you see on the screen in an Excel format. While in the displayed report you're limited to the top five to 10 rows, the downloaded report will have up to 2000 top records.  

Downloading a report will allow you to see reports from a broader range of time. The report is downloaded as an Excel spreadsheet based on the selected date filter. If you chose the past 28 days, the spreadsheet would have an individual tab for each day. The past 12 months download will have a tab for each month.

## Prevent filtering by country, occupation, department, or division

By default, users with global administrator, search administrator, and search editor roles can filter search data by country, occupation, or department/division. If you don't want administrators to filter your report data using these dimensions, you can go into your organizational settings in the Microsoft 365 admin center and configure this setting.  When this setting is unchecked, administrators won't be able to filter the **Query details** or **Connection analytics details** reports by these filters.  

Only global administrators can configure this setting.

To configure the setting:

1. In the Microsoft 365 admin center, select **Settings**, then select **Org Settings**. 
2. On the Org Setting page, select **Search & intelligence usage analytics**. 
3. On the Search & intelligence usage analytics page, uncheck **Allow usage reports to be filtered by country, occupation, department, or division**.
4. Select **Save**.

## Related articles

[Microsoft Search Usage Report - Queries](queries-usage-reports.md)</br>
[Microsoft Search Usage Report - Users](users-search-reports.md)</br>
[Microsoft Search Usage Report - Connection analytics](connection-analytics-reports.md)</br>
[Microsoft Search Usage Report - Answer analytics](answer-analytics-usage-reports.md)</br>
[View search usage reports in modern sites](/sharepoint/view-search-usage-reports-modern-sites)

