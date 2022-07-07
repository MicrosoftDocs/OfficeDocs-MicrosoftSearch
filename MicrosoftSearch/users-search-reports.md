---
title: "Microsoft Search Usage Report – Users"
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
description: "Review Microsoft Search Users usage reports"
---

# Microsoft Search Usage Report – Users

In the [Microsoft Search Usage Report](usage-reports.md), the Users section shows the total number of active and engaged users who have performed searches for the search application and date range selected by with the filters at the top of the page.  

- **Engaged users** - Users that have searched at least five days during a month and are only shown when a 12 month date range is selected.
- **Active users** – Users that search at least one day per month.

:::image type="content" source="media/usage-reports/users-reports.png" alt-text="A dashboard page showing a bar chart and a graph chart." lightbox="media/usage-reports/users-reports.png":::

The users search data is provided in the following reports: 

- **User engagements by application** – This bar chart shows the total number of active and engaged users by search application (Office.com, SharePoint start page, or Bing.com). 
- **Active users over time** – This graph shows the number of active users who searched using search applications over the specified time period.  

You can click the **Download report** link to download the report as an Excel file and see more details. 

## User details

The User details page shows how many people in your organization are active or engaged search users, measured by the filters you select.  These filters include: 

| Filter | Description |
|:-----|:-----|
|Date range |The date range for the analytics shown on the page. Available options are 7 days, 14 days, 31 days,  and last 12 months.|
|Search application  |The search application used to perform the queries.  Available options are SharePoint start page, Office.com, Bing.com (work tab), or all three applications combined.  |
|Country  |The country of the user performing query based on their **country** attribute in Azure Active Directory. |
|Occupation    |The occupation of the user performing the query based on their **title** attribute in Azure Active Directory.  |
|Department or division    |The department or division of the user performing the query, based on the **department** attribute of the second top-level user in the management chain of the user performing the search in Azure Active Directory. |

You can view the User details page by selecting **View Details** button at the bottom of the **Users** section of the Usage analytics main page. 

The user details page contains the following two charts:
- Active Users 
- Engaged Users   

### Active Users chart
The Active users chart shows you the total number of active users by search application. 

:::image type="content" source="media/usage-reports/active-users-chart.png" alt-text="A graph chart showing active users by search application." lightbox="media/usage-reports/active-users-chart.png":::

### Engaged Users chart
The Engaged users chart shows you the total number of engaged users by search application. 

:::image type="content" source="media/usage-reports/engaged-users-chart.png" alt-text="A graph chart showing engaged users by search application." lightbox="media/usage-reports/engaged-users-chart.png":::

## Download reports
Each report and table have a download option that allows you to download the background data for the report that you see on the screen in an Excel format. Where the displayed report is limited to the top five to ten rows, the downloaded report will have up to 2000 top records.   

Downloading a report will allow you to see reports from a broader range of time. The report is downloaded as an Excel spreadsheet based on the selected date filter. If you chose the past 7, 14, or 31 days, the spreadsheet would have an individual tab for each day. The past 12 months download will have a tab for each month.

## Related Topics

[Microsoft Search Usage Report](usage-reports.md)</br>
[Microsoft Search Usage Report-Queries](queries-usage-reports.md)</br>
[Microsoft Search Usage Report-Connection analytics](connection-analytics-reports.md)</br>