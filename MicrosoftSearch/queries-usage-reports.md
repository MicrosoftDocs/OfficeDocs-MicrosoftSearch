---
title: "Microsoft Search Usage Report – Queries "
ms.author: efrene    
author: efrene
manager: scotv
ms.topic: article
ms.service: mssearch
audience: Admin
ms.audience: Admin
ms.date: 07/07/2022 
ms.localizationpriority: medium
ms.collection:
- scotvorg
search.appverid:
- BFB160
- MET150
- MOE150
description: "Review the Microsoft Search usage - Queries reports"
---

# Microsoft Search Usage Report – Queries

In the [Microsoft Search Usage Report](usage-reports.md), the **Query analytics** section compares the number of search queries that had been clicked, abandoned, or had returned no results. It also compares queries by other factors, such as occupation, department, or division. The charts are presented for the filters selected on the top of the page.  

:::image type="content" source="media/usage-reports/query-analytics-key-metrics.png" alt-text="A dashboard showing key metrics for queries." lightbox="media/usage-reports/query-analytics-key-metrics.png":::

The data above the chart shows changes over the selected time period for the following metrics: 

|Metric | Description |
|:-----|:-----|
|Total queries  |The total number of search queries performed. |
|Average result position   |Represents the average position of clicked items in a search result list where the number one represents the top position (the lower the value, the better).|
|Click-through rate |The percentage of queries where the user has clicked on one or more of the answers or search results (the higher the value, the better)  |

The Recent Search Activity chart shows trending activity over time for the query count and click-through query rate. For example, if the 28-day filter is selected, this will compare the current 28-day period data to the previous 28-day period data. In the case of downward trend, the arrow and the line are shown in red. In the case of upward trend, it's shown in green. Trend data isn't available for a 12-month view. 

## Query Distribution

:::image type="content" source="media/usage-reports/queries-report.png" alt-text="A dashboard page containing four pie charts with query report data." lightbox="media/usage-reports/queries-report.png":::

The query data is provided in four charts:

- **Total queries by user action** – Compares the number of queries with no results with the number of queries where a user clicked on a result or performed no action (abandoned).  
- **Total queries by country** – Compares search queries by users in different countries based on a user’s **country** Microsoft Entra ID. 
- **Total queries by occupation** – Compares the number of search queries by users in different occupations based on their **title** attribute in Microsoft Entra ID.
- **Total queries by department or division** – Compares the number of search queries by users in different departments or divisions in your organization. This is based on the **department** attribute of the second top-level user in the management chain of the user performing the search in Microsoft Entra ID. 

Each chart shows the top five values, and the remaining values are summarized in the **Others** category. You can click the **Download report** link to download the report as an Excel file and see more details. 

## Query Details page

The Query details page shows the top search queries by people in your organization who use search regularly, along with queries that returned no results or were abandoned by the user without selecting any search results.

You can view the Query details page by selecting the **View Details** button at the bottom of the **Queries** section of the main usage analytics page.

:::image type="content" source="media/usage-reports/query-details.png" alt-text="A dashboard page showing three graph charts." lightbox="media/usage-reports/query-details.png":::

The three reports available to you on the query details page include:

- Most popular search terms
- Top-10 no-result queries
- Top abandoned search terms

In the **Filters** menu, use one or more of the following to filter the data in the reports: 

| Filter | Description |
|:-----|:-----|
|Date range |The date range for the analytics shown on the page. Available options are Last 28 days, and Last 12 months.|
|Search application  |The search application where the user has performed the queries: SharePoint start page, SharePoint sites, Office (Microsoft 365 app), Bing, or all four applications combined.  |
|Country  |The country of the user performing query based on their **country** attribute in Microsoft Entra ID. |
|Occupation    |The occupation of the user performing the query based on their **title** attribute in Microsoft Entra ID.  |
|Department or division    |The department or division of the user performing the query, based on the **department** attribute of the second top-level user in the management chain of the user performing the search in Microsoft Entra ID. |

>[!NOTE]
> To protect privacy, if the selected filter combination results in queries that are performed by only five or fewer individuals, those results will not be included in any report.

### Most popular search terms

This report shows the top 10 most popular search queries. It shows the top queries along with the top three clicked results for each query. Use this report to understand what types of information your users are searching for and the performance of the top three results. 

Each top search item provides the following data. 

| Column | Description |
|:-----|:-----|
|Total queries  |Total number of times this query has been performed. |
|Click-through rate |The percentage of times someone selected a search result returned by this query.|
|Top results clicked |Link to each of the top three results selected for this query.</br>**Note**: Links are not available for bookmarks and other answer features.  |
|Result type  |The entity type of each of the top three results (for example, file, bookmark, or external).  |
|Result click-through|The percentage of times someone clicked on this search result out of the total number of clicks for this query.  |
|Average position of result  |The average relative position of this search result on the search results page. |

### Top-10 no-result queries

This report shows popular search terms that have returned no results. Use this report to identify search queries that might create user dissatisfaction and to improve content discoverability. You can then determine if creating an answer, like a bookmark, or ingesting new content through a Graph connector is the right action.  

> [!NOTE]
> There are cases where a search term can be represented in the no-result report, even if it has bookmarks or is listed as one of the most popular queries. One example is if a query is performed in a vertical where the bookmark is not displayed (for example, the “Sites” vertical).

### Top abandoned search terms

This report shows popular search terms that receive low click-through. Use this report to identify search queries that might create user dissatisfaction and to improve content discoverability. You can then determine if creating an answer, like a bookmark, or ingesting new content through a Graph connector is the right action.  

## Prevent filtering by country, occupation, department, or division

By default, users with global administrator, search administrator, and search editor roles can filter search data by country, occupation, or department/division. If you do not want administrators to filter your report data using these dimensions, you can go into your organizational settings in the Microsoft 365 admin center and configure this setting.  When this setting is unchecked, administrators will not be able to filter the **Query details** reports by these filters.  

Only global administrators can configure this setting. 

To configure this setting: 

1. In the Microsoft 365 admin center, select **Settings**, then select **Org Settings**.
2. On the Org Setting page, select **Search & intelligence usage analytics**. 
3. On the Search & intelligence usage analytics page, uncheck **Allow usage reports to be filtered by country, occupation, department, or division**.
4. Select **Save**. 

## Download reports

Each report and table have a download option that allows you to download the background data for the report that you see on the screen in an Excel format. Where the displayed report is limited to the top five to ten rows, the downloaded report will have up to 2000 top records.

Downloading a report will allow you to see reports from a broader range of time. The report is downloaded as an Excel spreadsheet based on the selected date filter. If you chose the past 28 days, the spreadsheet would have an individual tab for each day. The past 12 months download will have a tab for each month. 

### Special note for the Most popular search items download report

In the **Most popular search items** report, notice that in the user interface of the report you, a query can have up to three top results for each popular search term. When you download the report and view it in Excel, a search term with more than one top result will display with a row for each result. The first three columns will pertain to the query (for example, (query text, count, and clicks), and will be the same. The remaining columns in the rows for the search item will pertain to the specific results, and will vary.

:::image type="content" source="media/usage-reports/excel-report.png" alt-text="A Top queries report Excel spreadsheet showing multiple rows." lightbox="media/usage-reports/excel-report.png":::

Here is an overview of the columns in the downloadable report. The **Applies to** column specifies if the column value pertains to the **query** or to the **result**.

| Column | Applies to | Description |
|:-----|:--------|:-----|
|Query text |Query  |The top search term performed. |
|Count |Query |Total queries for this search term. |
|Clicks |Query |Total queries that have one or more clicks for this search term. | 
|URL |Result |URL of each of the top three search results. Note that URL is not available for bookmarks, external content, and other answer features.   |
|Display Name|Result |Will currently be empty. In the future it will be used to show the file name and caption of the answer item.  |
|Type |Result | Result type, such as file, bookmark, or acronym.|
|Impressions |Result |The number of times this particular result has been displayed for this query.  |
|Click through |Result | The number of times a result has been clicked for this query. |
|Average position of result |Result  |The average position a result has been displayed at for this query.  |

## Related Topics

[Microsoft Search Usage Report](usage-reports.md)</br>
[Microsoft Search Usage Report - Users](users-search-reports.md)</br>
[Microsoft Search Usage Report - Connection analytics](connection-analytics-reports.md)</br>
[Microsoft Search Usage Report - Answer analytics](answer-analytics-usage-reports.md)</br>
[View search usage reports in modern sites](/sharepoint/view-search-usage-reports-modern-sites)
