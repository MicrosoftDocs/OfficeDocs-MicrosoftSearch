---
title: "Customize the Microsoft Search page"
ms.author: anfowler
author: adefowler
manager: shohara
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Add search verticals and customize search results"
---
# Customize the Microsoft Search page

You can customize the search results that are shown to users when they search in **SharePoint**, **Office.com**, and **Microsoft Search in Bing** by creating search verticals and result types. Verticals make it easier for users to find the information they’ve got permission to see.  For example, you can create a search vertical for marketing analysis data from third-party software for your users in the marketing department. You can also define result types and customize the layout for this data.  

You can create verticals and result types  at these levels:

- Organization level – SharePoint Home, Office.com and Microsoft Search in Bing are at the organization level, because they are available for everyone in your organization, as long as they’ve got permission to see the results.
- Site level – You can also customize the search results for SharePoint sites collections. For example, you might want to allow your customer service employees to search for “Severity 1” incidents directly from their department’s SharePoint site.

## What’s a search vertical?

A search vertical refers to the tabs that display vertically when a user views their search results in SharePoint and Office.com, and Microsoft Search in Bing. You can customize search verticals to narrows down search results so that only a certain type of search results are is displayed. For example, you could create one vertical for executives and another vertical for marketing related content and another for sales department, based on the type of information that each group would want to have. You will be able to customize Microsoft search experience and add custom verticals to Microsoft Search pages which will appear on SharePoint, Office.com and Microsoft search in Bing. By default, Microsoft Search shows ‘All’, ‘People’, ‘Files’, and Sites. which are always present on the search page.  
Initially you can only show results from connected content in a custom vertical.

**DISCLAIMER:** Verticals and result types are currently in preview as a part of Microsoft Connectors preview. To find out more about the preview, see [Connectors Preview](connectors-preview.md). Follow the [Microsoft Graph Connectors Public Preview Interest Form]( https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbRxWYgu82J_RFnMMATAS6_chUNVYwNU1CMDNZUDBSSDZKWVo2RDJDRjRLQi4u) to sign up.

## Things to consider...

Before you start, make sure the connector has been indexed. It can take up to 48 hours, depending on the file size.

You can’t create a vertical for content residing in SharePoint or from content indexed by the FileShare connector . Learn how to index content(Link to Connector documentation).

At a high-level, there are 3 main steps for adding a vertical.

1. Create the vertical – In this step you’ll define the vertical’s name, content source, and scope of the content that it will search.
1. Define what the results for this vertical will look like using the layout tools.
1. Turn on - Display the vertical from the **Vertical** list page.  

## STEP 1: Create the search vertical

Once you start the wizard, you'll be guided through the steps to define the vertical's name, content source and scope of the content that it will search. The vertical is created in a disabled state.  You will enable the vertical later.

You can use a limited set of Keyword Query Language (KQL) syntax to narrow down the scope,the page shows the properties available to you. We recommend using free text-keywords and property restrictions with Boolean operators for creating the KQL.

### Create a vertical at the organization level

To create the vertical on Microsoft Search in SharePoint home, Bing or Office.com, follow these steps:

1. In the Microsoft 365 admin center go to **Settings** > **Microsoft Search** > **Verticals**.
1. Select **Add** to get started.  

### Create a vertical at the site level

1. On the SharePoint site where you want to create the vertical, go to **Settings**.
1. Select **Site information**, and then **View all site settings**.
1. Look for the **Microsoft Search** section, and then select **Configure Microsoft Search for this site collection**.
1. In the navigation pane, go to **Custom experience**, and then select the **Verticals** tab.
1. To add a vertical, select **Add**. <br>
OR <br>To edit a vertical, select it in the list.

Remember, verticals are created in a disabled state. You'll still need to enable them before users can see the verticals.

## STEP 2: Create the result types

You can define how results are displayed in the vertical by designing the layout using result types. The result layout let you show important information directly in the search results, so that users don't have to click on each result to see if they've found what they're looking for.

A search result type is a rule that causes distinct kinds of search results to be displayed in different ways. It consists of the following:

- *One or more conditions* to compare each search result against, such as the content source of the search result.  
- A *result layout* to use for search results that meet the conditions. The result layout controls the way in which all results that meet the conditions appear and behave on a search results page.

**You must create at least one result type for results to display on the vertical.** You can create multiple result types for each vertical, this allows you to use different layouts for different type of results. For example, you could customize “Severity 1” incidents to have more prominent colors and a larger font than “Severity 3” incidents.
  
### Create a result type at the organization level

1. In the Microsoft 365 admin center, go to **Setting** > **Microsoft Search**, and then select **Result type**.
1. To add a **Result type**, select **Add**. To edit a result type, select the result type in the relevant list.
 
### Create a results type at the site level

1. On the SharePoint site where you want to create the result type, go to **Settings**.
1. Select **Site information**, and then **View all site settings**. 
1. Look for the Microsoft Search section, and then select **Configure Microsoft Search for this site collection**.
1. In the navigation pane, go to **Custom experience**, and then select Result type tab.
1. To add a result type, select **Add**. <br> OR <br>To edit a result type, select the result type in the list.

### View the vertical after enabling

After you enable the vertical, it might take a while before you can view it.
If you want to wait after enabling it, you can append *cacheClear=true* to the URL in SharePoint and Office.com to view the vertical immediately.

## Troubleshooting

Here's a list of common issues you might encounter and actions for fixing them.


|Error  |Action  |
|---------|---------|
|Cache miss and hit for MRT and vertical     |         |
|Something went wrong     |         |
|Not seeing content source - no connections created     |         |
|Row4     |         |


## Next steps
[STEP 3: Customize the results layout](customize-results-layout.md)