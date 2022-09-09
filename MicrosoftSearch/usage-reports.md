---
title: "Search Usage Reports"
ms.author: efrene
author: efrene
manager: scotv
ms.topic: article
ms.service: mssearch
audience: Admin
ms.audience: Admin
ms.date: 
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
description: "Review Microsoft Search usage reports"
recommendations: false
---

# Microsoft Search Usage Reports

Search usage reports enable you to gain more understanding of how people in your organization are using Microsoft Search. The insights generated from these reports will help you take actions that will make search a more useful and delightful experience for all your users.   

The **Microsoft Search usage reports** include graphs and tables generated from searches that are executed from the SharePoint Start Page (the site with URL ending in /SharePoint.aspx), Office.com, and the work tab search boxes at Microsoft Search in Bing. You can see data from the last 7 days, last 14 days, last 31 days, or last 12 months.   

Currently you can filter these reports by country, occupation, department, or division. To protect privacy, if any filters show data for five or less individuals, those results won't be included in the search usage reports. In addition, these filters can be toggled on or off for the entire organization on the Org settings page, in case your organization has specific privacy requirements.  

:::image type="content" source="media/usage-reports/usage-analytics.png" alt-text="A dashboard containing pie charts, graphs, and search analytics report data." lightbox="media/usage-reports/usage-analytics.png":::

## How to get to the Microsoft Search usage reports? 

1. In the Microsoft 365 admin center, select **Settings**, then select **Search and Intelligence**.  
2. On the **Search and Intelligence** page, select the **Insights** tab, and then select **Usage Analytics**. 

The search usage reports are available to users with the **search admin**, **search editor** or **global administrator** roles.

## What reports are available to me? 

The Microsoft Search Usage Reports page provides you with search data through the following four reports:

- **Recent Search Activity** – This chart gives a quick view of how people are using search in your organization. 
- **Queries** – This section shows a breakdown of the query activity by user action, country, occupation, and department or division. It also allows you to go to a query details page to view and analyze the queries in more detail. 
- **Users** – This section shows the total number of unique users and engaged users who have performed searches for the search application and date range selected with the filters on the top of the page. It also allows you to go to a user details page to view and analyze the user's data in more detail.
- **Connection Analytics** – This section provides an analysis of your connections. Review queries and clicks that use search results from your connections. It also allows you to go to a connection analytics details page to view and analyze the connection data in more detail. 

You can view more details about the [Queries](queries-usage-reports.md), [Users](users-search-reports.md), and [Connection analytics](connection-analytics-reports.md) sections by clicking the links. 

> [!NOTE]
> These search usage reports show collective search data based on search traffic from Bing (work vertical), Office.com and the SharePoint start page. You can also view and analyze search usage reports for individual modern SharePoint sites through their respective site collection usage reports. For more information, see [View search usage reports in modern sites](/sharepoint/view-search-usage-reports-modern-sites).

## Recent Search Activity Report

In the Microsoft Search Usage Report, you can view a quick summary of how people are using search in your organization through the **Recent Search Activity** chart. 

:::image type="content" source="media/usage-reports/recent-search-activity.png" alt-text="A graph chart showing recent search activity data." lightbox="media/usage-reports/recent-search-activity.png"::: 

The data above the chart shows changes over the selected time period for the following metrics: 

| Metric | Description |
|:-----|:-----|
|Total queries |The total number of search queries performed.  |
|Daily active users |The total number of unique users that have performed queries.  |
|Average result position |Represents the average position of clicked items in a search result list where the number one represents the top position (the lower the value, the better).|
|Click-through rate |The percentage of queries where the user has clicked on one or more of the answers or search results (the higher the value, the better). |

The Recent Search Activity chart shows trending activity over time for the query count and click-through query rate. For example, if the 7-day filter is selected this will compare the current 7-day period data to the previous 7-day period data. In the case of downward trend, the arrow and the line are shown in red. In the case of upward trend, it's shown in green. Trend data isn't available for a 12 month view. 

## Filters
At the top of the Recent Search Activity chart, you can use the following metrics to filter your data. Note that these filters will also apply to not only the Recent Search Activity chart, but also the other reports on the Microsoft Search usage reports page. 

| Filter | Description |
|:-----|:-----|
|Date Range |The date range for the analytics shown on the page: Last 7 days, Last 14 days, Last 31 days and Last 12 months.  |
|Search application |The search application where the user has performed the queries: SharePoint start page, Office, Bing, or all of those three search applications.  |

### Accessing search data prior to the start of new generation reports 

Processing of the new search usage reports varies for different tenants. If you select a date range prior to the date processing started, you'll see a message stating **Data not available for entire time period selected**. To view data prior to this date, you need to use the previous usage analytics reports. 

:::image type="content" source="media/usage-reports/data-not-available.png" alt-text="Data not available message." lightbox="media/usage-reports/data-not-available.png":::

To view the previous search analytics reports, select the **New usage reports** toggle on the top right corner of the page. 

:::image type="content" source="media/usage-reports/new-usage-toggle.png" alt-text="A toggle button." lightbox="media/usage-reports/new-usage-toggle.png":::

## You can download reports
Each report and table in the Microsoft Search Usage Reports page has a download option that allows you to download the background data for the report that you see on the screen in an Excel format. While in the displayed report you're limited to the top five to ten rows, the downloaded report will have up to 2000 top records.  

Downloading a report will allow you to see reports from a broader range of time. The report is downloaded as an Excel spreadsheet based on the selected date filter. If you chose the past 7, 14, or 31 days, the spreadsheet would have an individual tab for each day. The past 12 months download will have a tab for each month

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
[View search usage reports in modern sites](/sharepoint/view-search-usage-reports-modern-sites)


