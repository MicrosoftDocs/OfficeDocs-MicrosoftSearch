---
title: "Search Usage Reports- Analytics"
ms.author: nkagole
author: nataliekagole
manager: scotv
ms.topic: article
ms.service: mssearch
audience: Admin
ms.audience: Admin
ms.date: 7/31/2023 
ms.localizationpriority: medium
ms.collection:
- scotvorg
search.appverid:
- BFB160
- MET150
- MOE150
description: "Review Microsoft Search Answer Analytics Reports"
recommendations: false
---

# Microsoft Search Usage Reports - Answer Analytics

In the [Microsoft Search Usage Report](/microsoftsearch/usage-reports), the Answer analytics section gives you information on how the editorial Bookmarks, Acronyms and Q&A are performing within the organization.  

:::image type="content" source="media/usage-reports/answer-analytics.png" alt-text="A dashboard showing usage reports for answer analytics." lightbox="media/usage-reports/answer-analytics.png":::


The data above the chart shows changes over the selected time period for the following metrics:   



| Metric | Description |
|:-----|:-----|
|Queries with Answer Impressions |Number of queries that included one or more editorial answer impressions namely Bookmarks, Acronyms or Q&As.   |
|Bookmark Clicks |Number of queries where the user has clicked on a bookmark result.  |

The **Answer usage bar** graph shows the split of Answer impressions by Answer Type. Use this graph to understand the popular Answer category in your organization.  

You can view the **Answer Analytics details** page by selecting the **View answer analytics** button at the bottom of this section or by selecting the **Answer analytics tab** on the Overview page.  

## Answer analytics details page 

The Answer analytics details page provides you with details on Bookmark, Acronym and Q&A impressions trends, average impressions and number of items that are above and below the average impressions. These metrics are also available at an individual answer level. For example, you can use these reports to know how a particular Bookmark like “Outlook web” is performing.  

In the **Filters** menu, use one or more of the following to filter the data in the reports:

| Filter| Description |
|:-----|:-----|
|Date Range |The date range for the analytics shown on the page. Available options are Last 28 days and Last 12 months   |
|Search Application |The search application where the user has performed the queries: SharePoint start page, SharePoint sites, Office (Microsoft 365 app), Bing, or all four applications combined.   |

The **Answer Analytics** details page contains the following three reports for each Bookmarks, Acronyms and Q&As. 

**Bookmark Analytics**

- Bookmark impressions and click through rate trends. 
- Average click rate and number of items that are above and below the average click rate. 
- Impressions, click rate and user queries list of individual bookmarks.  

 **Acronym Analytics** 

- Acronym impressions and Acronym impressions trend for Admin curated and System curated acronyms. 
- Average impressions and number of items that are above and below the average impression number. 
- Impressions and user queries list of individual admin curated acronyms. 

 **Q&A Analytics** 

- Q&A impressions and Q&A impressions trend. 
- Average impressions and number of items that are above and below the average impression number. 
- Impressions and user queries list of individual Q&As. 

## Bookmarks Usage Report

The Bookmarks section provides information on average impressions, click through rate trends for bookmarks as a whole and for individual bookmark items that have impressed in the selected time period for the selected search application.  


### Bookmarks impressions and click through trends 

Use this graph to understand the bookmark impressions and click trends within your organization. 

:::image type="content" source="media/usage-reports/answer-analytics-bookmarks-usage.png" alt-text="A dashboard showing usage reports for bookmark impressions and click through trends." lightbox="media/usage-reports/answer-analytics-bookmarks-usage.png":::

| Metric| Description |
|:-----|:-----|
|Bookmark Impressions |Number of searches where a bookmark was shown to users. |
|Bookmark clicks  |Number of searches where the user has clicked on a bookmark when it was shown to the user.  |
|Average Click Through  |Average Click Through = [Total clicks in the selected time period/Time period in days] For example, in a selected time period of seven days, it's [Total clicks in seven days/seven] |

### Average click rate
Use the Average click rate to segregate the bookmarks that are performing well and bookmarks that need updates to improve the click rate.  

:::image type="content" source="media/usage-reports/answer-analytics-bookmark-insights.png" alt-text="A dashboard showing bookmark insights." lightbox="media/usage-reports/answer-analytics-bookmark-insights.png":::

| Metric| Description |
|:-----|:-----|
|Average click rate  |Average click rate = [Bookmark clicks]/[Bookmark impressions]. For example, in a selected time period of seven days, Average click rate is the [total bookmark clicks in seven days]/[total bookmark impressions in seven days]. This is represented as a percentage. |
|Bookmarks above average  |Number of Bookmarks that have a click rate that is above the Average click rate. These Bookmarks are performing well.
|Bookmarks below average   |Number of Bookmarks that have a click rate that is below or equal to the Average click rate. These Bookmarks have potential for improvement.  |
### Bookmark Item Insights

The Bookmark item insights table provides information on how individual bookmarks are performing. This table lists all the bookmarks that have impressed in the selected time period for the selected search application.

:::image type="content" source="media/usage-reports/answer-analytics-bookmark-item-insights.png" alt-text="A dashboard showing bookmark item insights." lightbox="media/usage-reports/answer-analytics-bookmark-item-insights.png":::

| Metric| Description |
|:-----|:-----|
|Usage status   |This label indicates if the bookmark is above or below the Average click rate.   |
|Usage (click through)   |Click through or Average click rate here is calculated as [Clicks]/[Impressions] for the bookmark in the selected period   |
|Impressions |Number of times the bookmark was shown to users
|Clicks | Number of times the bookmark received a click when it was shown to users    |
|Top user query (s)  |List of user queries that triggered the bookmark to show up for the user    |

A detailed list of user queries for a bookmark is available in the details panel page for each bookmark item.

:::image type="content" source="media/usage-reports/answer-analytics-bookmark-queries.png" alt-text="A dashboard showing a detailed list of bookmark user queries." lightbox="media/usage-reports/answer-analytics-bookmark-queries.png":::

## Acronyms Usage Report  

The Acronyms section provides information on impressions trends for acronyms as whole and for individual acronyms that have impressed in the selected time period. Acronyms can include both admin curated and system curated acronyms. [Learn more about acronym curation](/microsoftsearch/manage-acronyms#set-up-acronyms-answers)

:::image type="content" source="media/usage-reports/answer-analytics-acronyms-usage-reports.png" alt-text="A dashboard showing acronyms usage reports." lightbox="media\usage-reports\answer-analytics-acronyms-usage-reports.png":::

| Metric| Description |
|:-----|:-----|
|Admin curated  |Number of searches where admin curated acronyms were shown to users  |
|System curated  |Number of searches where system curated acronyms were shown to users 

### Acronyms Impressions Trends
Use this graph to understand the acronym impression trends within your organization. The graph shows trends for both admin curated and system curated acronyms. 

:::image type="content" source="media/usage-reports/answer-analytics-acronyms-impressions-trends.png" alt-text="A dashboard showing acronyms impressions trends over time." lightbox="media/usage-reports/answer-analytics-acronyms-impressions-trends.png":::

| Metric| Description |
|:-----|:-----|
|Admin curated impressions  |Number of searches where admin curated acronyms were shown to users, represented as a line chart. |
|System curated impressions   |Number of searches where system curated acronyms were shown to users, represented as a line chart. 

### Average Impressions 
Use Average impressions to segregate acronyms that are performing well and acronyms that need improvements to improve the impression. The Average impressions and Acronym item insights apply only to admin curated acronyms. 

:::image type="content" source="media/usage-reports/answer-analytics-average-impressions-insights.png" alt-text="A dashboard showing avergae impressions." lightbox="media/usage-reports/answer-analytics-average-impressions-insights.png":::

| Metric| Description |
|:-----|:-----|
|Average impressions   |Average Impressions= [sum of all admin curated acronym impressions]/[sum of all unique admin curated acronyms that have impressed]. For example, in a selected time period of seven days, Average impressions is the [total admin curated acronym impressions in seven days]/[sum of all unique admin curated acronyms that have impressed in seven days].  |
|Acronyms above average   |Number of admin curated acronyms that are above the Average impressions number. 
|Acronyms below average     |Number of admin curated acronyms that are below or equal to the Average impressions number. 

### Acronym Item Insights 
The Acronym item insights table provides information on how individual admin curated acronyms are performing. This table lists all admin curated acronyms that have impressed in the selected time-period for the selected search application. 

:::image type="content" source="media/usage-reports/answer-analytics-acronym-item-insights.png" alt-text="A dashboard showing acronym item insights." lightbox="media/usage-reports/answer-analytics-acronym-item-insights.png":::

| Metric | Description |
|:-----|:-----|
|Usage status  |This label indicates if the acronym is above or below the Average impression number.    |
|Usage (impressions)  |Usage here's the number of acronym impressions.  |
|Impressions  |Number of searches where the acronym was shown to users.|
|Top user query(s) |List of user queries that triggered the acronym to show up for the user.  |

Detailed list of user queries is available in the details panel for each acronym item.

:::image type="content" source="media/usage-reports/answer-analytics-acronym-usage-user-queries.png" alt-text="A dashboard showing acronym usage-user-queries ." lightbox="media/usage-reports/answer-analytics-acronym-usage-user-queries.png":::

## Q&A Usage Report 
The Q&A section provides information on impressions trends for Q&As as a whole and for individual Q&A items that have impressed in the selected time period and for the search application.  
### Q&A Impressions Trends 
Use this graph to understand the Q&A impression trends within your organization. 

:::image type="content" source="media/usage-reports/answer-analytics-q&a-impression-trends.png" alt-text="A dashboard showing q&a impression trends over time ." lightbox="media/usage-reports/answer-analytics-q&a-impression-trends.png":::

| Metric | Description |
|:-----|:-----|
|Q&A impressions   |Number of searches where Q&As were shown to users    |

### Average Impressions 
Use Average impressions to segregate Q&As that are performing well and Q&As that need improvements to improve the impression.  

:::image type="content" source="media/usage-reports/answer-analytics-average-impressions-q&a-insights.png" alt-text="A dashboard showing average impressions based on q&a usage ." lightbox="media/usage-reports/answer-analytics-average-impressions-q&a-insights.png":::

| Metric | Description |
|:-----|:-----|
|Average impressions   |Average Impressions= [sum of all Q&A impressions]/[sum of all unique Q&As that have impressed]. For example, in a selected time period of seven days, Average impressions is the [total Q&A impressions in seven days]/[sum of all unique Q&As that have impressed in seven days]    |
|Q&As above average   |Number of Q&As that have an impressions count that is above the Average impressions number.  |
|Q&As below average   |Number of Q&As that have an impressions count that is below or equal to the Average impressions number. |

### Q&A Item Insights 

The Q&A item insights table provides information on how individual Q&As are performing. This table lists all the Q&As that have impressed in the selected time period for the selected search application. 

:::image type="content" source="media/usage-reports/answer-analytics-q&a-item-insights.png" alt-text="A dashboard showing q&a item insights ." lightbox="media/usage-reports/answer-analytics-q&a-item-insights.png":::

| Metric | Description |
|:-----|:-----|
|Usage status    |This label indicates if the Q&A is above or below the Average impression number.  |
|Usage (impressions)    |Usage here's the number of Q&A impressions.   |
|Impressions    |Number of searches where the Q&A was shown to users.  |
|Top user query (s)     |List of user queries that triggered the Q&A to show up for the user.   |

Detailed list of user queries for which the Q&A impressed is available in the details panel page for each Q&A item. 

:::image type="content" source="media/usage-reports/answer-analytics-q&a-usage-user-queries.png" alt-text="A dashboard showing q&a usage for the last 31 days." lightbox="media/usage-reports/answer-analytics-q&a-usage-user-queries.png":::


> [!NOTE]
> Answer Analytics is currently not supported for the 12-month filter range and for certain types of tenants. In case you do not see Answer Analytics feature on your test tenant drop us an email at searchadminxteam@service.microsoft.com and we will reach out to you for further investigation.

## Related articles

[Microsoft Search Usage Report](usage-reports.md)</br>
[Microsoft Search Usage Report - Queries](queries-usage-reports.md)</br>
[Microsoft Search Usage Report - Users](users-search-reports.md)</br>
[Microsoft Search Usage Report - Connection analytics](connection-analytics-reports.md)</br>
[View search usage reports in modern sites](/sharepoint/view-search-usage-reports-modern-sites)


[def]: media/usage-reports/answer-analytics.png
