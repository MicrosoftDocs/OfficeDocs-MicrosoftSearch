---
title: "Microsoft Search Usage Report – Connection analytics"
ms.author: efrene
author: efrene
manager: scotv
ms.topic: article
ms.service: mssearch
audience: Admin
ms.audience: Admin
ms.date: 10/15/2024 
ms.localizationpriority: medium
ms.collection:
- scotvorg
search.appverid:
- BFB160
- MET150
- MOE150
description: "Review Microsoft Search usage connection analytics report."
---

# Microsoft Search Usage Report – Connection analytics

In the [Microsoft Search Usage Report](usage-reports.md), the **Connection analytics** section provides an overview of graph connector usage in your organization. It highlights metrics about how often users search for third party content and engage with it.

:::image type="content" source="media/usage-reports/connection-analytics.png" alt-text="A report dashboard that shows graphs and tables of search usage for connection analytics." lightbox="media/usage-reports/connection-analytics.png":::

The data above the chart shows changes over the selected time period for the following metrics:

| Metric | Description |
|:-----|:-----|
|Active connection |The number of connections that are currently active. |
|Total indexed items |Total number of indexed items across all connections. |
|Queries with connection results|Number of queries that included one or more connection results. |
|Click-through queries  |Number of queries where the user has clicked on one or more of the connection results. |
|Unique users |Number of users who query at least once for graph connectors.|
|Return rate |Unique users who have searched for connector at least once or more in the 7-day period.|

## Queries and queries with clicks

The **Queries and click-throughs over time** graph shows the number of queries with connection results and how many of those queries received a click. See the following definitions:

- **Queries** - The number of queries where connector results.
- **Queries with clicks** - How many of the queries with connector results received a click.  
- **Total impressions** – Total number of times connector results were shown to users for any query.

You can select the **Download report** link to download the report as an Excel file and see more details.  

You can view the **Connection Analytics details** page by selecting the **Connection analytics tab** or selecting the **View connection analytics** button at the bottom of the Connection analytics section of the Usage analytics main page.  

## Connection analytics details page

The Connection analytics details page allows you to analyze queries with search results from your connections.

:::image type="content" source="media/usage-reports/connection-analytics-details.png" alt-text="A report dashboard that shows graphs and tables of search usage for connection analytics details reports." lightbox="media/usage-reports/connection-analytics-details.png":::

In the **Filters** menu, use one or more of the following to filter the data in the reports:

| Filter | Description |
|:-----|:-----|
|Date range |The date range for the analytics shown on the page. Available options are Last 28 days, and Last 12 months.|
|Search application  |The search application where the user has performed the queries: SharePoint start page, SharePoint sites, Office (Microsoft 365 app), Bing, or all four applications combined. |
|Country  |The country of the user performing query based on their **country** attribute in Microsoft Entra ID. |
|Occupation    |The occupation of the user performing the query based on their **title** attribute in Microsoft Entra ID.  |
|Department or division    |The department or division of the user performing the query, based on the **department** attribute of the second top-level user in the management chain of the user performing the search in Microsoft Entra ID. |

The Connection analytics details page contains the following three reports:

- Queries and click-throughs by connection
- Total indexed items by connection
- Connections

### Queries and click-throughs by connection

This report shows a comparison of the number of queries with connection results and the number of queries that received one or more clicks for up to six of the most frequently used data connections.

:::image type="content" source="media/usage-reports/queries-clicks-by-connection.png" alt-text="A bar chart graph that shows queries and click through data by connection type.":::

### Total indexed items by connection

This report shows a comparison of total indexed items used by each of the data connections.  

:::image type="content" source="media/usage-reports/index-by-connection.png" alt-text="A bar chart graph that shows indexed items by data connection.":::

### Connections

This report shows the details (connection type, queries with connection results, click through queries, and indexed items) for all the connections that have been created. It analyzes queries with search results from the connections, which helps to identify which connections are valuable to the organization. These critical metrics are useful to adopt graph connectors, identify potential areas for tuning, and justify the investments and connection quota.

:::image type="content" source="media/usage-reports/connections.png" alt-text="A table that shows details about your connections." lightbox="media/usage-reports/connections.png":::

## Download reports

Each report and table have a download option that allows you to download the background data for the report that you see on the screen in an Excel format. Where the displayed report is limited to the top five to ten rows, the downloaded report will have up to 2000 top records.  

Downloading a report will allow you to see reports from a broader range of time. The report is downloaded as an Excel spreadsheet based on the selected date filter. If you chose the past 28 days, the spreadsheet would have an individual tab for each day. The past 12 months download will have a tab for each month.

## Prevent filtering by country, occupation, department, or division

By default, users with global administrator, search administrator, and search editor roles can filter search data by country, occupation, or department/division. If you do not want administrators to filter your report data using these dimensions, you can go into your organizational settings in the Microsoft 365 admin center and configure this setting.  When this setting is unchecked, administrators will not be able to filter the **Connection analytics details** reports by these filters.  

Only global administrators can configure this setting.

To configure this setting: 

1. In the Microsoft 365 admin center, select **Settings**, then select **Org Settings**.
2. On the Org Setting page, select **Search & intelligence usage analytics**. 
3. On the Search & intelligence usage analytics page, uncheck **Allow usage reports to be filtered by country, occupation, department, or division**.
4. Select **Save**. 

## Related Topics

[Microsoft Search Usage Report](usage-reports.md)</br>
[Microsoft Search Usage Report - Queries](queries-usage-reports.md)</br>
[Microsoft Search Usage Report - Users](users-search-reports.md)</br>
[Microsoft Search Usage Report - Answer analytics](answer-analytics-usage-reports.md)</br>
[View search usage reports in modern sites](/sharepoint/view-search-usage-reports-modern-sites)
