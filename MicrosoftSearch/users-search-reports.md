---
title: "Microsoft Search Usage Report – User analytics"
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
description: "Review Microsoft Search Users usage reports"
---

# Microsoft Search Usage Report – User analytics

In the [Microsoft Search Usage Report](usage-reports.md), the **User analytics** section shows how people in your organization use Microsoft Search and allows you to compare user engagement and adoption across the search applications and time periods. The charts are presented for the filters selected on the top of the page.


:::image type="content" source="media/usage-reports/users-reports.png" alt-text="A dashboard page showing a bar chart and a graph chart." lightbox="media/usage-reports/users-reports.png":::

The key metrics show you a quick summary of how people are using search in your organization. The data shows metrics and changes from the previous period for the following metrics.


## User analytics detail pages

The User analytics details page shows how  people in your organization use Microsoft Search, measured by the filters you select.  These filters include:

| Filter | Description |
|:-----|:-----|
|Date range |The date range for the analytics shown on the page. The available options are Last 28 days, and Last 12 months.|
|Search application  |The search application where the user has performed the queries: Windows Search Work results, Microsoft Search for Bing, Outlook, Teams, OneDrive, Word/Excel/Powerpoint, SharePoint start page, SharePoint sites, Microsoft365.com, Bing, or all applications combined. |
|Country  |The country of the user performing query based on their **country** attribute in Azure Active Directory. |
|Occupation    |The occupation of the user performing the query based on their **title** attribute in Azure Active Directory.  |
|Department or division    |The department or division of the user performing the query, based on the **department** attribute of the second top-level user in the management chain of the user performing the search in Azure Active Directory. |

You can view the User details page by selecting the **User analytics** tab or selecting the **View user analytics** button at the bottom of the **User analytics** section of the Usage analytics main page.  

In addition to the user analytics graphs shown on the summary page (covered above), the user details page contains the following additional two charts:

- Search users by geography
- Top 10 search users by occupation
- Top 10 search users by department or division

### Search users by geography 

The Search users by geography chart shows you a distribution of search users based on their country attribute in Azure Active Directory and for the selected set of filters.

:::image type="content" source="media/usage-reports/active-users-chart.png" alt-text="A graph chart showing active users by search application." lightbox="media/usage-reports/active-users-chart.png":::

### Top 10 search users by occupation

The Top 10 search users by occupation chart shows top you a distribution of search users based on their **title** attribute in Azure Active Directory and for the selected set of filters. Note that due to computational complexity, only the top 100 occupations are included in this list which means that some filter combinations might produce an empty list of occupations. 

:::image type="content" source="media/usage-reports/engaged-users-chart.png" alt-text="A graph chart showing engaged users by search application." lightbox="media/usage-reports/engaged-users-chart.png":::

## Top 10 search users by department or division  
The Top 10 search users by department or division chart shows top you a distribution of search users based on the **department** attribute of the second top-level user in the management chain of the user performing the search in Azure Active Directory and for the selected set of filters.

## User analytics – See what actions you can take 
The **User analytics** section shows how people in your organization use Microsoft Search and allows you to compare user engagement and adoption across the search applications and time periods. Use the graphs to: 

- Validate key metrics for users who searched, users searching weekly and users with no search activity. What is the potential in increasing users searching weekly and addressing users with no search activity? 

- Check the user engagement. Is it as expected? 

- Check the distribution of search activity across all search applications. Where do you have gaps in search adoption? 

- Visit the user analytics detail page for more insights and use the filters to identify adoption gaps. What search application, region or department are lagging in search adoption? Would awareness or training help? 

By monitoring user adoption and addressing adoption gaps, you can optimize the value that search is bringing to each individual and the entire organization. 

## Accessing search data prior to the start of new generation reports 
Processing of the new search user reports varies for different tenants. If you select a date range prior to the date processing started, for example by selecting the 12 month date range, you might see a message stating **Data not available for entire time period selected.** To view data prior to this date, you need to use the previous user analytics reports. 

To view the previous search analytics reports, select the **New user analytics** toggle on the top right corner of the page.

# IMAGE 

## Prevent filtering by country, occupation, department, or division 

By default, users with global administrator, search administrator, and search editor roles can filter search data by country, occupation, or department/division. If you do not want administrators to filter your report data using these dimensions, you can go into your organizational settings in the Microsoft 365 admin center and configure this setting. When this setting is unchecked, administrators will not be able to filter the **Query details** reports by these filters. 

Only global administrators can configure this setting. 

To configure this setting: 

1. In the Microsoft 365 admin center, select **Settings**, then select **Org Settings**. 

2. On the Org Setting page, select **Search & intelligence usage analytics**. 

3. On the Search & intelligence usage analytics page, uncheck  **Allow usage reports to be filtered by country, occupation, department, or division**. 

4. Select **Save**. 

 


## Related Topics

[Microsoft Search Usage Report](usage-reports.md)</br>
[Microsoft Search Usage Report - Queries](queries-usage-reports.md)</br>
[Microsoft Search Usage Report - Connection analytics](connection-analytics-reports.md)</br>
[View search usage reports in modern sites](/sharepoint/view-search-usage-reports-modern-sites)
