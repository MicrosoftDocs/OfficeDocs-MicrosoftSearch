---
title: "Microsoft Search Overview"
ms.author: bstucker
author: bstuck
manager: bstucker
ms.audience: Admin
ms.topic: overview
ms.service: mssearch
ms.localizationpriority: medium
ms.collection: essentials-overview
ms.date: 03/11/2022
search.appverid:
- BFB160
- MET150
- MOE150
description: "Get an overview of what Microsoft Search is, its benefits, and which apps support Microsoft Search."
---
# Overview of Microsoft Search

Microsoft Search helps you find what you need to complete what you're working on. Whether you're searching for people, files, organization charts, sites, or answers to common questions, you can use Microsoft Search throughout your workday to get answers.

Microsoft Search helps users find the right answers, people, and content to complete their tasks in the app they're already working in.

- Users get results that are relevant in the **context** of the app they search from. For example, when they search in [Microsoft Outlook](https://www.microsoft.com/outlook), they find emails, and not [SharePoint](https://sharepoint.com/) sites. When they search in SharePoint, they find sites, pages, and files.
- Whichever app users are working in; Microsoft Search is **personal**. Microsoft Search uses insights from the [Microsoft Graph](https://developer.microsoft.com/graph/) to show results that are relevant to each user. Each user might see different results, even if they search for the same words. They only see results that they already have access to, Microsoft Search doesn't change permissions.
- When in [Bing](https://bing.com), users get results from within their organization in addition to the public web results.

## What users see

In [Bing](https://bing.com), users use the same search box as for web searches. In the Office apps, users find the Microsoft Search box in the header bar. It looks like this:

![Screenshots of app windows with Microsoft Search box in the header bar.](media/Headings_520.png)

When users click in the **Search** box, search suggests results based on their previous activity in Office 365 and based on content that's trending in your organization. Search considers activities such as files they were working on recently, commands they've used recently, and people they collaborate with. As users start typing in the **Search** box, the suggested results update. Users can open search results right from the **Search** box. Here's an example of a search in [SharePoint](https://sharepoint.com/).

![Screenshots of the Microsoft Search box with a query and suggested results.](media/SERP_text_520.png)

If the suggestions in the search box aren't what users are looking for, **Enter** opens the full list of results. They can use metadata such as who last modified the item and when and where the item is located to determine if it's what they're looking for.

![Screenshots of the Microsoft Search results page.](media/search_box.png)

## Benefits of Microsoft Search

**Search across Microsoft 365 from any Microsoft Search box** – Users can search from any Microsoft Search box and get quickly back to what they were doing. Microsoft Search brings together results from data sources in Office 365, including [SharePoint](https://sharepoint.com/), [Microsoft OneDrive for Business](https://onedrive.live.com/about/business/), and [Microsoft Exchange](https://products.office.com/exchange/microsoft-exchange-server).

**Easy to search** – Microsoft Search suggests results based on users' previous activity in Office 365, right in the **Search** box.

**Find shared files** – Microsoft Search uses advanced query understanding to make finding shared files simple. Users can easily find files they're collaborating on.

**Show relevant content** – Promote the information and answers your users need to complete tasks, for example policies, benefits, resources, tools, and more. You can also target specific groups, like new hires, remote workers, or different geographies.

**Administer across all apps** – Microsoft Search is **on** by default and any administration you do applies to Microsoft Search in all the apps.

## Tailoring Microsoft Search to your organization

As an administrator you can create an amazing Microsoft Search experience for your users.

**Show useful content** – Answers provide fast, authoritative results to search queries based on keywords. [Plan your content](plan-your-content.md).

**Add external content** – Microsoft Graph Connectors allow you to bring external content into the index. Use connectors to enrich the search experience with data and files from outside of Microsoft 365. [Overview of Microsoft Graph connectors](connectors-overview.md)

**Customize the user experience** – You can customize the user experience by using verticals and other configurations. [Customize the Microsoft Search page](customize-search-page.md)

## What content is searched

Microsoft Search shows the content that your organization has stored in Microsoft 365 or has indexed through connectors. Microsoft Search doesn't search across tenants or show results from content that's shared by other organizations. If your organization has set up a hybrid SharePoint environment using cloud hybrid search, Microsoft Search returns search results from both online and on-premises SharePoint content, including any external content you've connected to your SharePoint Server environment. [Learn more about hybrid search environments](/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint).

Users will get the same search results they get from other locations and when using Microsoft Search in Bing they will also get results from the internet.

## How Microsoft Search works

When a user searches, Microsoft Search processes the query and parses search intent from larger phrases, using Artificial Intelligence (AI) to learn common superfluous phrases users add to their queries that don't impact their search intent. For example, when a user searches for "how to change my password" we extract the less important words from the query and trigger based on the relevant ones like "change password".  
The search results that the user has **permission** to see are presented on the search results page. Microsoft Search uses intelligent ranking algorithms to order results based on relevance.

## Privacy

In Microsoft Search only the content that a user has permission to see can appear in search results. A user might, for example, have permission to see a file because the user created it, it was shared with the user or with a larger group that includes the user, or it’s stored in a folder or location that the user has permission to access.
> [!NOTE]
> Learn how Microsoft Search in Bing protects your company data in [Security and Privacy for Microsoft Search in Bing](security-for-search.md).

When people filter on a person in SharePoint, they see results from content that the filtered person has worked on and that they have permission to see. If the filtered person or their organization have turned off item insights in Microsoft Graph, people only see results from content the filtered person has shared with them or from content that they both have worked on. [Learn about item insights](/graph/item-insights-overview).

When users get results for a search in Outlook, SharePoint Online, and Office.com, the issued query is recorded in their search history. A user’s search history is personal, it isn’t shared with your organization or with Microsoft. Their search history helps them quickly get back to things they’ve found before. As they type a query, matches in their search history are suggested back to them in the search box.  

Users can review their search history at any time by downloading it. They can also clear their history at any time. Both actions are done from the [My Account portal](https://myaccount.microsoft.com) of their work or school account. Go to the [Settings & Privacy page](https://myworkaccount.microsoft.com/privacy) and open the Microsoft Search section. Recording of history can’t be paused.

The Outlook search history contains their searches in Outlook, Outlook for mobile, and Outlook on the web. It serves the same suggested queries to all three endpoints. Their searches on SharePoint sites, on the SharePoint start page, and on the Office.com home page are combined into one history and the same queries are suggested back when they search either on the SharePoint start page or on the Office.com home page. Historic queries are not served when users search on SharePoint sites.

When many people in your organization search for the same thing in Microsoft Search in Outlook, SharePoint, and Office.com, you as an admin can see that the query is popular, but not who searched for it. You can use this information to define which resources are good results for popular queries and make search better for your organization. Learn about providing answers in [Plan your content](plan-your-content.md).

## See also

[Set up Microsoft Search](setup-microsoft-search.md)
