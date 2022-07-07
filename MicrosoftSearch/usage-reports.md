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
---

# Microsoft Search Usage Reports

Search usage reports enable you to gain more understanding of how people in your organization are using Microsoft Search. The insights generated from these reports will help you take actions that will make search a more useful and delightful experience for all your users.   

The **Microsoft Search usage reports** include graphs and tables generated from searches that are executed from the SharePoint Start Page (the site with URL ending in /SharePoint.aspx), Office.com, and the work tab search boxes at Microsoft Search in Bing. You can see data from the last 7 days, last 14 days, last 31 days, or last 12 months.   

Currently you can filter these reports by country, occupation, department, or division. To protect privacy, if any filters show data for five or less individuals, those results will not be included in the search usage reports. In addition, these filters can be toggled on or off for the entire organization on the Org settings page.  

:::image type="content" source="media/usage-reports/usage-analytics.png" alt-text="A dashboard containing pie charts, graphs, and search analytics report data." lightbox="media/usage-reports/usage-analytics.png":::

## How to get to the Microsoft Search usage reports 

1. In the Microsoft 365 admin center, select **Settings**, then select **Search and Intelligence**.  
2. On the **Search and Intelligence** page, select the **Insights** tab, and then select **Usage Analytics**. 

## What reports are available to me? 

The Microsoft Search Usage Reports page provides you with search data through the following four reports:

- **Recent Search Activity** - This chart gives a quick view of how people are using search in your organization. 
- **Queries** – This section compares the number of search queries clicked, abandoned, or returning no results. It also allows you to go to a query details page to view more detailed information. 
- **Users** - Total number of unique users and engaged users who have performed searches for the search application and date range selected with the filters on the top of the page. It also allows you to go to a user details page to view more detailed information.
- **Connection Analytics** – Provides an analysis of your connections. Review queries and clicks that use search results from your connections. It also allows you to go to a connection analytics details page to view more detailed information. 

You can view more details about the [Queries](queries-usage-reports.md), [Users](users-search-reports.md), and [Connection analytics](connection-analytics-reports.md) sections by selecting the links. 

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

The Recent Search Activity chart shows trending over time for the query count and click-through query rate. For example, if the 7-day filter is selected this will compare the current 7-day period data to the previous 7-day period data. In case of downward trend, the arrow and the line are shown in red, in case of upward trend, it is shown green. For 12 months there will not be any trend. 

## Filters
At the top of the Recent Search Activity chart, you can use the following metrics to filter your data. Note that these filters will also apply to not only the Recent Search Activity chart, but also the other reports on the Microsoft Search usage reports page. 

| Filter | Description |
|:-----|:-----|
|Date Range |The date range for the analytics shown on the page: Last 7 days, Last 14 days, Last 31 days and Last 12 months.  |
|Search application |The search application where the user has performed the queries: SharePoint start page, Office, Bing, or all of those three search applications.  |

### Accessing search data prior to 6/28/2022 

The new search usage reports were available on 6/28/2022. If you select a date range prior to this date, you will see a message stating **Data not available for entire time period selected**. To view data prior to this date, you need to use the previous usage analytics reports. 

:::image type="content" source="media/usage-reports/data-not-available.png" alt-text="Data not available message." lightbox="media/usage-reports/data-not-available.png":::

To use the previous search analytics reports, select the **New Usage Reports** toggle on the top right corner of the page. 

:::image type="content" source="media/usage-reports/new-usage-toggle.png" alt-text="A toggle button." lightbox="media/usage-reports/new-usage-toggle.png":::

## You can download reports
Each report and table in the Microsoft Search Usage Reports page has a download option that allows you to download the background data for the report that you see on the screen in an Excel format. While in the displayed report you are limited to the top five to ten rows, the downloaded report will have up to 2000 top records.  

Downloading a report will allow you to see reports from a broader range of time. The report is downloaded as an Excel spreadsheet based on the selected date filter. If you chose the past 7, 14, or 31 days, the spreadsheet would have an individual tab for each day. The past 12 months download will have a tab for each month

## Prevent filtering by country, occupation, department, or division
By default, tenant administrators can filter search data by country, occupation, or department/division. If you do not want search admins to filter your report data using these dimensions, you can go into your organizational settings in the Microsoft 365 admin center and configure this setting.  When this setting is unchecked, users with **search administrator** and **search editor** roles will not be able to filter the**Query details** or **Connection analytics details**”** reports by these filters.  

To configure the setting:
1. In the Microsoft 365 admin center, select **Settings**, then select **Org Settings**. 
2. On the Org Setting page, select **Search & intelligence usage analytics**. 
3. On the Search & intelligence usage analytics page, uncheck **Allow usage reports to be filtered by country, occupation, department, or division**.
4. Select **Save**. 

## Related articles

[Microsoft Search Usage Report-Queries](queries-usage-reports.md)</br>
[Microsoft Search Usage Report-Users](users-search-reports.md)</br>
[Microsoft Search Usage Report-Connection analytics](connection-analytics-reports.md)</br>


