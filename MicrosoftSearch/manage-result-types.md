---
title: "Manage Result Types"
ms.author: jeffkizn
author: jeffkizn
manager: parulm
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Managing result types in a search vertical"
---

# Understanding result types

You can define how results are displayed in a vertical by designing the layout using result types. The result layout lets you show important information directly in the search results, so users don't have to select each result to see if they found what they're looking for. Like verticals, result types are applicable only to content from Connectors.

## Default search result layout

A default search result layout will be shown for Connector content if **labels** and **content** property have been mapped correctly to the source properties at the time of configuring the connector. The label **title** is the most important label. It is **strongly recommended** that you have a property assigned to this label to use default search result layout.

## Create your own result type

You can decide to create your own search result layout and override the default search result layout by creating a **result type**. A search result type is a rule that causes distinct kinds of search results to be displayed in different ways. It consists of the following:

- **One or more conditions** to compare each search result against, such as the content source of the search result.  
- A **result layout** to use for search results that meet the conditions. The result layout controls the way that all results that meet the conditions appear and behave on a search results page.

**If appropriate mapping is not done to show default search result layout, You must create at least one result type for results to display on the vertical.** You can create multiple result types for each vertical, which allows you to use different layouts for different type of results. For example, you can customize *Severity 1* incidents to have more prominent colors and a larger font compared to *Severity 3* incidents.

After you start the wizard, you're guided through the steps to define the name, content source, and conditions for the result type. You can define the priority of the result type from the list view.
  
## Create a result type at the organization level

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to [**Result types**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/resulttypes).
1. To add a **Result type**, select **Add**. To edit a result type, select the result type in the relevant list.

## Create a results type at the site level

1. On the [SharePoint](https://sharepoint.com/) site where you want to create the result type, go to **Settings**.
1. Select **Site information** and then **View all site settings**.
1. Look for the Microsoft Search section, and then select **Configure Microsoft Search for this site collection**.
1. In the navigation pane, go to **Custom experience**, and select **Result type** tab.
1. To add a result type, select **Add**.  Or, to edit a result type, select the result type in the list.
