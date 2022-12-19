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

The [Microsoft Search usage reports](https://admin.microsoft.com/Adminportal/Home?#/MicrosoftSearch/insights) include graphs and tables generated from searches that are executed from the SharePoint Start Page, Office.com, and Bing. You can see data from the last seven days, last 14 days, last 31 days, or monthly for the previous year.

## Canvas Coverage

These are the search canvases that are currently included in tenant level usage reports:

| Search canvas | Description |
|:-----|:-----|
|Bing |The work tab in Microsoft Search in Bing is included.   |
|Office |The Microsoft 365 App (formerly known as the Office app) at office.com are included.  |
|SharePoint Sites |SharePoint Online, including both classic (enterprise/site/basic search center) and modern (hub, communication, and team) site searches. |
|SharePoint Start Page |The site available when selecting SharePoint in the Microsoft 365 app launcher with the URL ending in /SharePoint.aspx. |

You can filter reports by country, occupation, department, or division. To protect privacy, if any filters show data for five or less individuals, those results won't be included in the search usage reports. In addition, these filters can be toggled on or off for the entire organization on the Org settings page, in case your organization has specific privacy requirements.  

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

You can view more details about the [Queries](queries-usage-reports.md), [Users](users-search-reports.md), and [Connection analytics](connection-analytics-reports.md) sections by selecting the links.

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

### Filters

At the top of the Recent Search Activity chart, you can use the following metrics to filter your data. These filters will also apply to not only the Recent Search Activity chart, but also the other reports on the Microsoft Search usage reports page.

| Filter | Description |
|:-----|:-----|
|Date Range |The date range for the analytics shown on the page: Last seven days, Last 14 days, Last 31 days and Last 12 months.  |
|Search application |The search application where the user has performed the queries: SharePoint start page, Office, Bing, or all of those three search applications.  |

The Recent Search Activity chart shows trending activity over time for the query count and click-through query rate. For example, if the 7-day filter is selected, this will compare the current 7-day period data to the previous 7-day period data. In the case of downward trend, the arrow and the line are shown in red. In the case of upward trend, it's shown in green. Trend data isn't available for a 12 month view.

## Queries

The total queries section compares the number of search queries clicked, abandoned, or returning no results. It also compares queries by other factors, such as occupation, department, or division. The charts are presented for the filters selected on the top of the page.

:::image type="content" source="media/usage-reports/usage-analytics-queries-section.png" alt-text="The Queries section in Microsoft Search Usage Reports" lightbox="media/usage-reports/usage-analytics-queries-section.png":::

Here's an overview of metrics presented in this section:

| Metric | Description |
|:-----|:-----|
|By user action |Compare the number of queries with no-result with the number of queries where a user clicked on a result or performed no action (abandoned).  |
|By country |Compare search queries by users in different countries based on a user’s “country” Azure Active Directory (Azure Ad) attribute.  |
|By occupation |Compare search queries by users in different occupations based on a user’s “title” Azure Active Directory (Azure Ad) attribute.|
|By department or division |Compare search queries by users in different departments or divisions. Department or division is rolled up in the reporting chain to the “department” Azure Active Directory (Azure Ad) attribute of the person reporting to CEO (top level). |

Note that the pie charts will show the top five values. Other values are summarized in the “Others” category. The downloadable report provides more details.

Selecting the **View details** button will take you to the **Query details** page, which provides details like “most popular queries," “top no-result queries," and “top abandoned queries." See [Query details](#query-details-page) on this page to learn more.

## Users

This section represents the total number of unique users and engaged users who have performed searches for the search application. You can also view the date range selected with the filters on the top of the page. Engaged users are defined as users that have searched at least five days during a month, and are only shown when a 12-month date range is selected.

:::image type="content" source="media/usage-reports/usage-analytics-users-section.png" alt-text="The Users section in Microsoft Search Usage Reports" lightbox="media/usage-reports/usage-analytics-users-section.png":::

To see trend graphs for active and engaged users, select **View details** to go to the User details page. See [User details](#user-analytics-details) on this page to learn more.

## Connection analytics

The report shows how the connections defined in the data sources tab in the Search and Intelligence admin center performed with user queries.

:::image type="content" source="media/usage-reports/usage-analytics-connection-analytics-section.png" alt-text="The Connection Analytics section in Microsoft Search Usage Reports" lightbox="media/usage-reports/usage-analytics-connection-analytics-section.png":::

Here's an overview of metrics presented in this section:

| Metric | Description |
|:-----|:-----|
|Queries with connection results |Number of queries that included one or more connection results.  |
|Click-through queries |Number of queries where the user has clicked on one or more of the connection results.  |
|Total indexed items |Total number of indexed items across all connections.|
|Active connections |The number of connections that are currently active. |
|Queries and click-throughs over time |Trend graph over the selected time period showing the number of queries with connection results and the number of queries where the user clicked on one or more of the connection results. |

The **View details** button will take you to the **Connection details** page, which provides “queries and click-throughs by connection, “total indexed items by connection,” and “overview of connections." See [Connection details](#connection-analytics-details) on this page to learn more.

## Query details page

This page shows the top search queries from your organization, along with queries that returned no results or were otherwise abandoned by the user without selecting any search results.

To go to the Query details page, select the **View Details** button at the bottom of the **Queries** section of the Usage analytics main page.

:::image type="content" source="media/usage-reports/usage-analytics-query-details.png" alt-text="The Queries details page in Microsoft Search Usage Reports" lightbox="media/usage-reports/usage-analytics-query-details.png":::

The reports on this page can be filtered along one or more of the following dimensions.

| Filter | Description |
|:-----|:-----|
|Date range |The date range for the analytics shown on the page. Available options are “seven days”, “14 days”, “31 days” and “last 12 months”.  |
|Search application |The search application is used to perform the queries. Available options are SharePoint start page, SharePoint sites, Office.com, Bing.com (work tab), or all three applications combined.  |
|Country |The country of the user performing the query based on their “country” attribute in Azure Active Directory (Azure Ad). |
|Occupation |The occupation of the user performing the query based on their “title” attribute in Azure Active Directory (Azure Ad). |
|Department or division |The department or division of the user performing the query, based on the “department” attribute of the second top-level user in the management chain of the user performing the search in Azure Active Directory (Azure Ad). |

>[!NOTE]
> To protect privacy, if the selected filter combination results in queries that are performed by only five or fewer individuals, those results will not be included in any report.

### Most popular search terms

This report shows the top 10 most popular search queries. It shows the top queries along with the top three clicked results for each query. Use this report to understand what types of information your users are searching for and the performance of the top three results.

Each top search term provides the following data for the selected filters:

| Filter | Description |
|:-----|:-----|
|Total queries |Total number of times this query has been performed.  |
|Click-through rate |The percentage of times someone selected a search result returned by this query. |
|Top results clicked |Link to each of the top three results selected for this query. Note: Links aren't available for bookmarks and other answer features. |
|Result type |The entity type of each of the top three results, e.g., File, Bookmark, External. |
|Result click-through |The percentage of times someone clicked on this search result out of the total number of clicks for this query. |
|Average position of result |The average relative position of this search result on the search results page where on average this search result appeared on the page of search results for this query. |

### Top 10 no-result queries

This report shows popular search terms that have returned no results. Use this report to identify search queries that might create user dissatisfaction and to improve content discoverability. You can then determine if creating an answer, like a bookmark, or ingesting new content through a Graph connector is the right action.

>[!NOTE]
> There are cases where a search term can be represented in the no-result report, even if it has bookmarks and even if it is also listed as one of the most popular queries. One example is if a query is performed in a vertical where the bookmark is not displayed. For example, the “Sites” vertical.

### Top abandoned search terms

This report shows popular search terms that receive low click-through. Use this report to identify search queries that might create user dissatisfaction and to improve content discoverability. You can then determine if creating an answer, like a bookmark, or ingesting new content through a Graph connector is the right action.

## User analytics details

This page shows how many people in your organization are active or engaged search users, measured by the filters chosen. Engaged monthly users are defined as users that search at least five days per month, while active users are users that search at least one day per month.

To go to the User analytics details page, select the **View Details** button at the bottom of the **Users** section on the Usage analytics main page.

:::image type="content" source="media/usage-reports/usage-analytics-users-details.png" alt-text="The User details page in Microsoft Search Usage Reports" lightbox="media/usage-reports/usage-analytics-users-details.png":::

>[!NOTE]
> The Engaged users graph is only shown for a date range of 12 months.

The reports on this page can be filtered along one or more of the following dimensions:

 Filter | Description |
|:-----|:-----|
|Date range |The date range for the analytics shown on the page: 7 days, 14 days, 31 days and last 12 months.  |
|Search application |The search application where the user has performed the queries: SharePoint start page, SharePoint sites, Office.com, Bing.com (work tab), or all  three search applications.  |

## Connection analytics details

This page allows you to analyze queries with search results from your connections.

To go to the Connection analytics details page, select the **View details** button at the bottom of the **Connection analytics** section on the Usage analytics main page.

:::image type="content" source="media/usage-reports/usage-analytics-connection-analytics-details.png" alt-text="The Connection Analytics details page in Microsoft Search Usage Reports" lightbox="media/usage-reports/usage-analytics-connection-analytics-details.png":::

Filter | Description |
|:-----|:-----|
|Date range |The date range for the analytics shown on the page: 7 days, 14 days, 31 days and last 12 months. |
|Search application |The search application where the user has performed the queries: SharePoint start page, SharePoint sites, Office.com, Bing.com (work tab), or all of those three search applications. |
|Country |The country of the query based on a user’s “country” Azure Active Directory (Azure Ad) attribute. |
|Occupation |The occupation of the user performing the query based on a user’s “title” Azure Active Directory (Azure Ad) attribute. |
|Department or division |The department or division of the user performing the query. Department or division is rolled up in the reporting chain to the “department” Azure Active Directory (Azure Ad) attribute of the person reporting to CEO (top level). |

### Queries and click-throughs by connection

This report shows a comparison of the number of queries with connection results and the number of queries that received one or more clicks for up to six of the most frequently used data connections.

### Total indexed items by connection

This report shows a comparison of total indexed items used by each of the data connections.

### Connections

This report shows the details (connection type, queries with connection results, click through queries, and indexed items) for all the connections that have been created. It analyzes queries with search results from the connections, which helps to identify which connections are valuable to the organization. These critical metrics are useful to adopt graph connectors, identify potential areas for tuning, and justify the investments and connection quota.

### Accessing search data prior to the start of new generation reports

Processing of the new search usage reports varies for different tenants. If you select a date range prior to the date processing started, you'll see a message stating **Data not available for entire time period selected**. To view data prior to this date, you need to use the previous usage analytics reports.

:::image type="content" source="media/usage-reports/data-not-available.png" alt-text="Data not available message." lightbox="media/usage-reports/data-not-available.png":::

To view the previous search analytics reports, select the **New usage reports** toggle on the top right corner of the page. 

:::image type="content" source="media/usage-reports/new-usage-toggle.png" alt-text="A toggle button." lightbox="media/usage-reports/new-usage-toggle.png":::

## You can download reports

Each report and table in the Microsoft Search Usage Reports page has a download option that allows you to download the background data for the report that you see on the screen in an Excel format. While in the displayed report you're limited to the top five to 10 rows, the downloaded report will have up to 2000 top records.  

Downloading a report will allow you to see reports from a broader range of time. The report is downloaded as an Excel spreadsheet based on the selected date filter. If you chose the past 7, 14, or 31 days, the spreadsheet would have an individual tab for each day. The past 12 months download will have a tab for each month.

### Special note for the Most popular search terms download report

Notice that the report presented on the screen allows an expansion of up to three top results for each popular search term. In Excel, this will be represented as rows with some duplicated values, which means that you might see up to three copies of the first columns in the Excel report.

:::image type="content" source="media/usage-reports/excel-report.png" alt-text="Excel report showing top queries" lightbox="media/usage-reports/excel-report.png":::

Here's an overview of the columns in this report where it’s specified if the specific column value refers to the “query” or the “result”:

Column | Applies to | Description |
|:-----|:-----|:-----|
|Query text |Query |The top search term performed |
|Count |Query |Total queries for this search term |
|Clicks |Query |Total queries that have one or more clicks for this search term |
|URL |Result |URL of each of the top three search results. URL isn't available for bookmarks, external content, and other answer features. |
|Display name |Result |Will currently be empty. For future use to show the file name and caption of the answer item. |
|Type |Result |Result type, e.g., File, bookmark, acronym, etc.|
|Impressions |Result |The number of times this particular result has been displayed for this query. |
|Click through |Result |The number of times a result has been clicked for this query. |
|Average position of result |Result |The average position a result has been displayed at for this query.|

## Organization setting: Filters toggle

A new setting has been introduced to allow tenant administrators to disable filtering (country, occupation, department/division) on the usage analytics reports from a privacy perspective. For example, if your organization doesn't want the search admin to have access to slice the reports by the provided dimensions, use this setting. When this setting is unchecked, users with “search administrator” and “search editor” roles won't be able to filter the “Query details” or “Connection analytics details” reports by these filters.

:::image type="content" source="media/usage-reports/usage-analytics-organization-toggle.png" alt-text="The toggle to disable filtering in Microsoft Search Usage Reports":::

The [organization setting](https://admin.microsoft.com/Adminportal/Home#/Settings/Services/:/Settings/L1/SearchIntelligenceAnalytics) is available in the Microsoft 365 admin center under **Settings** > **Org settings** > **Search & intelligence usage analytics**.

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
