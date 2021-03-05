---
title: "Microsoft Search Overview"
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
description: "Get an overview of what Microsoft Search is, its benefits, and which apps support Microsoft Search."
---
# Overview of Microsoft Search

Microsoft Search helps you find what you need to complete what you're working on. Whether you're searching for people, files, org charts, sites, or answers to common questions, you can use Microsoft Search throughout your workday to get answers.

Microsoft Search helps users find the right answers, people, and content to complete their tasks in the app they're already working in.

- Users get results that are relevant in the **context** of the app they search from. For example, when they search in [Microsoft Outlook](https://www.microsoft.com/outlook), they find emails, and not [SharePoint](http://sharepoint.com/) sites. When they search in SharePoint, they find sites, pages, and files.
- Whichever app users are working in; Microsoft Search is **personal**. Microsoft Search uses insights from the [Microsoft Graph](https://developer.microsoft.com/graph/) to show results that are relevant to each user. Each user might see different results, even if they search for the same words. They only see results that they already have access to, Microsoft Search doesn't change permissions.
- Users don't need to remember where the information is located. For example, a user is working in [Microsoft Word](https://products.office.com/word) and wants to reuse information from a presentation that a colleague shared from their [OneDrive](https://onedrive.live.com/about/). There's no need to switch to OneDrive and search for that presentation, they can simply search from Word.
- When in [Bing](https://bing.com), users get results from within their organization in addition to the public web results.

## What users see

In [Bing](https://bing.com), users use the same search box as for web searches. In the Office apps, users find the Microsoft Search box in the header bar. It looks like this:

![Screenshots of app windows with Microsoft Search box in the header bar](media/Headings_520.png)

When users click in the **Search** box, search suggests results based on their previous activity in Office 365 and based on content that's trending in your organization. Files they were working on recently, commands they've used recently as well as people they collaborate with are examples of activity that search considers. As users start typing in the **Search** box, the suggested results update. Users can open search results right from the **Search** box. Here's an example of a search in [SharePoint](http://sharepoint.com/).

![Screenshots of the Microsoft Search box with a query and suggested results](media/SERP_text_520.png)

If the suggestions in the search box aren't what users are looking for, **Enter** opens the full list of results. They can use metadata such as who last modified the item and when, where the item is located, as well as preview it to determine if it's what they're looking for.

![Screenshots of the Microsoft Search results page](media/search_box.png)

## Benefits of Microsoft Search

**Search across Microsoft 365 from any Microsoft Search box** – Users can search from any Microsoft Search box and get quickly back to what they were doing. Microsoft Search brings together results from data sources in Office 365, including [SharePoint](http://sharepoint.com/), [Microsoft OneDrive for Business](https://onedrive.live.com/about/business/), and [Microsoft Exchange Server](https://products.office.com/exchange/microsoft-exchange-server).

**Easy to search** – Microsoft Search suggests results based on users' previous activity in Office 365, right in the **Search** box.

**Find shared files** – Microsoft Search uses advanced query understanding to make finding shared files simple. Users can easily find files they're collaborating on.

**Show relevant content** – Promote the information and answers your users need to complete tasks, for example policies, benefits, resources, tools, and more. You can also target specific groups, like new hires, remote workers, or different geographies.

**Administer across all apps** – Microsoft Search is **on** by default and any administration you do applies to Microsoft Search in all the apps.

## Tailoring Microsoft Search to your organization

As an administrator you can create an amazing Microsoft Search experience for your users.

**Show useful content** – Answers provide fast, authoritative results to search queries based on keywords. [Plan your content](plan-your-content.md).

**Add external content** – Microsoft Graph Connectors allow you to bring external content into the index. Use connectors to enrich the search experience with data and files from outside of Microsoft 365. [Overview of Microsoft Graph connectors](connectors-overview.md)

**Customize the user experience** – You can customize the user experience through the use of verticals and other configurations. [Customize the Microsoft Search page](customize-search-page.md)

## What content is searched

Microsoft Search shows the content that your organization has stored in Microsoft 365 or indexed through connectors. Microsoft Search does not search across tenants or show results from content that's shared by other organizations. If your organization has set up a hybrid SharePoint environment using cloud hybrid search, Microsoft Search returns search results from both online and on-premises SharePoint content, including any external content you've connected to your SharePoint Server environment. [Learn more about hybrid search environments](https://docs.microsoft.com/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint).

Users will get the same search results they get from other locations and will also get results from the internet.

## How Microsoft Search works

When a user searches, Microsoft Search processes the query and parses search intent from larger phrases, using Artificial Intelligence (AI) to learn common superfluous phrases users add to their queries that don't impact their search intent. For example, when a user searches for "how to change my password" we extract the less important words from the query and trigger based on the relevant ones like "change password".  
The search results that the user has **permission** to see are presented on the search results page. Microsoft Search uses intelligent ranking algorithms to order results based on relevance.

## How Microsoft Search in Bing protects your company data

[Security and Privacy for Microsoft Search in Bing](security-for-search.md)

## See also

[Set up Microsoft Search](setup-microsoft-search.md)
