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
# Customize the search results page

By creating search verticals and result types, you can customize the search results that are shown to users when they search in [SharePoint](http://sharepoint.com/), [Microsoft Office](https://Office.com), and Microsoft Search in [Bing](https://Bing.com). Verticals make it easier for users to find the information they’ve got permission to see. For example, you can create a search vertical for marketing analysis data from third-party software for your users in the marketing department. You can also define result types and customize the layout for this data.  

You can create verticals and result types at these levels: 

- **Organization level** – When you add a vertical at the organization level, it appears on the search results page when users search from their [SharePoint](http://sharepoint.com/) start page, on [Office](https://Office.com), and on [Bing](https://Bing.com). 
- **Site level** – For example, you might want to allow your customer service employees to search for **Severity 1** incidents directly from their department’s SharePoint site. 

## What’s a search vertical?

At the top of the Microsoft Search results page is a row of tabs that are the search verticals. A search vertical only shows results of a certain type or from certain content. An example is only files or news. By default, Microsoft Search shows the verticals **All**, **People**, **Files**, **Sites**, and **News**.  

You can add search verticals that are relevant to your organization. These will appear on the Microsoft Search results page in [SharePoint](http://sharepoint.com/), [Office](https://Office.com), and [Bing](https://Bing.com). For example, you could create one vertical for marketing-related content and another for sales, based on the type of information that each group would want to have. You can add verticals to show results only from content indexed via connectors.  

**DISCLAIMER:** Verticals and result types are currently in preview as a part of the Microsoft Graph connectors preview. You can't create a vertical for content residing in [SharePoint](http://sharepoint.com/) or from content indexed by the [file share connector](file-share-connector.md). To find out more about the preview, see [Connectors Preview](connectors-preview.md). To participate in the preview, you must first submit the [Microsoft Graph Connectors Preview Signup form](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbRxWYgu82J_RFnMMATAS6_chUNVYwNU1CMDNZUDBSSDZKWVo2RDJDRjRLQi4u).

## Things to consider...

Before you start, make sure the connector has been indexed. It can take up to 48 hours, depending on the file size.

You can’t create a vertical for content residing in [SharePoint](http://sharepoint.com/) or from content indexed by the [file share connector](file-share-connector.md). Learn how to [index content](configure-connector.md).

At a high level, there are three main steps for adding a vertical: 

1. Create the vertical. In this step, you define the vertical’s name, content source, and scope of the content to search. 
2. Define what the results for this vertical will look like.  
3. Enable the vertical (to be displayed) from the vertical list page.   

## STEP 1: Create the search vertical

After you start the wizard, you're guided through the steps to define the vertical's name, content source, and scope of the content that it will search. The vertical is created in a disabled state. You'll enable the vertical later.

You can use a limited set of the [Keyword Query Language (KQL)](https://docs.microsoft.com/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference) to narrow down the scope, and the page lists the properties available to you. We recommend using free text-keywords and property restrictions with boolean operators for creating the KQL. 

### Create a vertical at the organization level

To create the vertical on Microsoft Search in [SharePoint](http://sharepoint.com/) home, [Office](https://Office.com), or [Bing](https://Bing.com), follow these steps:

1. In the Microsoft 365 [admin center](https://admin.microsoft.com), go to **Settings** > **Microsoft Search** > **Verticals**.
1. Select **Add** to get started.  

### Create a vertical at the site level

1. On the [SharePoint](http://sharepoint.com/) site where you want to create the vertical, go to **Settings**.
1. Select **Site information** and then **View all site settings**.
1. Look for the **Microsoft Search** section, and then select **Configure Microsoft Search for this site collection**.
1. In the navigation pane, go to **Custom experience**, and then select the **Verticals** tab.
1. To add a vertical, select **Add**. <br>
OR <br>To edit a vertical, select it in the list.

Remember, verticals are created in a disabled state. You still need to enable them before users can see the verticals.

## STEP 2: Create the result types

You can define how results are displayed in the vertical by designing the layout using result types. The result layout lets you show important information directly in the search results, so that users don't have to select each result to see if they've found what they're looking for.

A search result type is a rule that causes distinct kinds of search results to be displayed in different ways. It consists of the following:

- **One or more conditions** to compare each search result against, such as the content source of the search result.  
- A **result layout** to use for search results that meet the conditions. The result layout controls the way in which all results that meet the conditions appear and behave on a search results page.

**You must create at least one result type for results to display on the vertical.** You can create multiple result types for each vertical, which allows you to use different layouts for different type of results. For example, you can customize **Severity 1** incidents to have more prominent colors and a larger font compared to **Severity 3** incidents. 

After you start the wizard, you're guided through the steps to define the name, content source, and conditions for the result type. You can define the priority of the result type from the list view. 
  
### Create a result type at the organization level

1. In the [admin center](https://admin.microsoft.com), go to **Setting** > **Microsoft Search**, and then select **Result type**.
1. To add a **Result type**, select **Add**. To edit a result type, select the result type in the relevant list.
 
### Create a results type at the site level

1. On the [SharePoint](http://sharepoint.com/) site where you want to create the result type, go to **Settings**.
1. Select **Site information** and then **View all site settings**. 
1. Look for the Microsoft Search section, and then select **Configure Microsoft Search for this site collection**.
1. In the navigation pane, go to **Custom experience**, and then select **Result type** tab.
1. To add a result type, select **Add**. <br> OR <br>To edit a result type, select the result type in the list.

### View the vertical after enabling

After you enable the vertical, it might take a while before you can view it.
If you do not want to wait after enabling it, you can append **cacheClear=true** to the URL in [SharePoint](http://sharepoint.com/) and [Office](https://Office.com) to view the vertical immediately.

## Troubleshooting

Here's a list of common issues you might encounter and actions for fixing them.


|Error  |Action  |
|---------|---------|
|I see a *Something went wrong* error on the vertical. |   Both vertical and result types are needed to complete the setup. Make sure you have created both for the same content source.      |
|Why don't I see my result layout, although I have created one? | It takes a few minutes for result types to be used as these settings are generally cached. Wait for a few minutes and try again.        |
|I don't see any content sources on the vertical or result type page.     |      Make sure you have configured connectors and indexed data.   |



## Next steps
[STEP 3: Customize the results layout](customize-results-layout.md)
