---
title: "Microsoft Search Overview"
ms.author: tlarsen
author: tlarsen
manager: mnirkhe
ms.date: 12/11/2018
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Priority
search.appverid:
- BFB160
- MET150
- MOE150
description: "Get an overview of what Microsoft Search is, it's benefits, and which apps that currently have Microsoft Search."
---
# Overview of Microsoft Search

Microsoft Search is the unified search capability in the Microsoft 365 productivity apps and the broader Microsoft ecosystem. Over time Microsoft Search will be available in more and more apps across Microsoft 365.

Microsoft Search helps users find the right answers, people, and content to complete their tasks in the app they’re already working in.

- Users get results that are relevant in the **context** of the app they search from. For example, when they search in Outlook, they find emails, not sites in SharePoint. When they search in SharePoint, they find sites, pages, and files.
- Whichever app users are working in; Microsoft Search is **personal**.  Microsoft Search uses insights from the Microsoft Graph to show results that are relevant to each user. Each user might see different results, even if they search for the same words. They only see results that they already have access to, Microsoft Search doesn’t change permissions.
- Users don’t need to remember where the information is located. For example, a user is working in Word and wants to reuse information from a presentation that a colleague shared from their OneDrive. There’s no need to switch to OneDrive and search for that presentation, they can simply search from Word.  
- When in Bing, users get results from within their organization in addition to the public web results .

## What users see

In Bing, users use the same search box as for web searches. In the Microsoft 365 apps, users find the Microsoft Search box in the header bar. It looks like this:

![Screenshots of app windows with Microsoft Search box in the header bar](media/Headings_520.png)


When users click in the search box, search suggests results based on their previous activity in Office 365 and based on content that’s trending in your organization. Files they were working on recently, commands they’ve used recently as well as people they collaborate with are examples of activity that search considers. As users start typing in the search box, the suggested results update. Users can open search results right from the search box. Here's an example of a search in SharePoint.

![Screenshots of the Microsoft Search box with a query and suggested results](media/search_box.png)

If the suggestions in the search box aren’t what they’re looking for, **Enter** opens the full list of results. They can use metadata such as who last modified the item and when, where the items is located, as well as preview it to determine if it’s what they’re looking for.

![Screenshots of the Microsoft Search results page](media/SERP_text_520.png)

## Benefits of Microsoft Search

**Search across Microsoft 365 from any Microsoft Search box** – Users can search from any Microsoft Search box and get quickly back to what they were doing. Microsoft Search brings together results from data sources in Office 365, including SharePoint, OneDrive for Business, and Exchange.

**Easy to search** - Microsoft Search suggests results based on users’ previous activity in Office 365, right in the search box.

**Find shared files** - Microsoft Search uses advanced query understanding to make finding shared files simple. Users can easily find files they’re collaborating on.

**Show relevant content** - Promote the information and answers your users need to complete tasks, for example policies, benefits, resources, tools, and more. You can also target specific groups, like new hires or remote workers.

**Microsoft Search evolves** – The set of content types users can search for and the intelligence of the search box will grow over time.

**Administer across all apps** - Microsoft Search is **on** by default and any administration you do applies to Microsoft Search in all the apps.

## Apps that currently have Microsoft Search

 The following Office 365 apps currently offer Microsoft Search:

- SharePoint Online
- OneDrive for Business
- Outlook on the web
- Office apps on Windows

In addition, users find Microsoft Search in:

- Bing
- Office.com
- The starting pages for Word, Excel, and PowerPoint Online

Users can also initiate a search in Bing from the Edge address bar.

## Requirements

Your organization must have an Office 365 tenant with one of the following subscriptions:

- Office 365 Business Essentials and Business Premium
- Office 365 A1/A3/A5
- Office 365 Education E1/E3
- Office 365 Enterprise E1/E3/E3 developer/E5
- Office 365 F1
- Microsoft 365 Business
- Microsoft 365 A3/A5
- Microsoft 365 F1/E3/E5

Both users and search administrators must be licensed with one of these subscriptions. Only users with active accounts can use Microsoft Search, and they must be **signed in**.

## Tailoring Microsoft Search to your organization

As an admin you can make it easy for your users to get good organization-specific results when they search from their SharePoint start page, Office.com, or Bing. You administer Microsoft Search in the Microsoft 365 admin center.

**Show useful content** - Help users find important tools and resources within your organization by bookmarking them. Just as you can create a bookmark to a public webpage, you can create a bookmark for any internal webpage, which your users can search for. You can also integrate a Power App in the bookmark so users can complete their task directly from the bookmark.

**Offer answers to common questions** – Give the best answer for the most frequently asked questions in your organization. When users enter a common question in the search box, Microsoft Search shows the answer as a result instead of just providing a link to the web page.

**Show useful locations** - Show map results and address information for your organization's buildings, offices, and other workspaces on a map. Users can use the maps to get directions, see what's nearby, and more.

## What content is searched?

Microsoft Search searches in content that’s stored in SharePoint Online, OneDrive for Business, and Exchange, including people from the global address list and Office 365 groups. If your organization has set up a hybrid SharePoint environment using cloud hybrid search, Microsoft Search returns search results from both online and on-premises SharePoint content, including any external content you’ve connected to your SharePoint Server environment. [Learn more about hybrid search environments](https://docs.microsoft.com/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint).

When users search from the SharePoint start page or Office.com, Microsoft Search searches across all the content in their organization and presents all the results it finds. This is known as the **global search scope**.

When users search from Bing, users get the most relevant results from all the content in their organization embedded in the list of results from the **web**. If they need to see **all** organizational results, the global search scope is only a click away.

## What types of results can users find?
Users find the following types of results when they search from:

**SharePoint**: Files, folders, people in your organization, organization charts, sites, site pages, news, lists and list items. If defined, answers to common questions, bookmarks that lead to authoritative information, locations, and tools. [Learn which types of files you can find](https://docs.microsoft.com/en-us/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types).

**Office.com and Word, Excel, and PowerPoint Online start pages**: Apps, files, folders, people, organization charts, SharePoint sites, site pages, lists and list items. If defined, answers to common questions, bookmarks that lead to authoritative information, locations, and tools. Files of the same type as in SharePoint can be found.

**Bing**: Content on the public web, files, Office 365 groups, people, Yammer and Teams conversations, organization charts, SharePoint sites. If defined, answers to common questions, bookmarks that lead to authoritative information, locations, and tools.  Word, Excel, PowerPoint, Visio, OneNote, and PDF files can be found.

**Outlook**: Emails, attachments, and people in your organization.

**Office apps on Windows**: Actions in the app, people in your organization and on the web, files, word explanations, matches for the query inside the file or in help content, content on the web. Word, Excel, PowerPoint, Visio, and OneNote files can be found.

**OneDrive**: Files of the same type as in SharePoint can be found.

## How does Microsoft Search work?

When a user searches, Microsoft Search processes the query and parses search intent from larger phrases, using Artificial Intelligence (AI) to learn common superfluous phrases users add to their queries that don't impact their search intent. For example, when a user searches for "how to change my password" we extract the less important words from the query and trigger based on the relevant ones like "change password".  

The search results that the user has **permission** to see are presented on the search results page. Microsoft Search uses intelligent ranking algorithms to order results based on relevance.

## Microsoft Search in SharePoint

Microsoft Search in SharePoint is the modern search experience in SharePoint Online. SharePoint Online also offers a classic search experience. Both experiences are on by default and both search the same content. As a search administrator you can’t turn on either experience in SharePoint Online. Which search experience your users get depends on where they search from:

- Users get the Microsoft Search box on the SharePoint start page, hub sites, communication sites, and modern team sites.
- Users get the classic search box on publishing sites, classic team sites, and in the Search Center.

You can customize the classic search experience, for example by adding custom refiners to the search results page or displaying a certain type of result differently. You can’t customize the Microsoft Search experience in SharePoint like that. Some of the customizations you make for classic search might impact Microsoft Search in SharePoint. If your organization will use both search experiences in SharePoint, [learn about the differences and how to avoid impacting Microsoft Search in SharePoint](https://docs.microsoft.com/en-us/sharepoint/differences-classic-modern-search).

## Microsoft Search in Bing

Because work-related searches may be sensitive, Microsoft Search uses a set of trust measures for how these searches are handled by the public web results part of Bing.

Regardless of whether a user query contains one or more work-related results in the returned response, the following measures are taken:

**Logging** - All search logs pertaining to Microsoft Search traffic are de-identified and stored separately from public, non-Microsoft Search traffic. They're retained for 18 months, and access is restricted for debugging purposes only. The queries in these logs are not used to model or train public features such as autosuggest or related searches for the public web. Restricted access is managed via various secure mechanisms, including security groups and other layers within the engineering system.

**Search history** - When signed in with a work or school account, a user's search history won't be available on other computers or devices.

**Advertising** - Enterprise search queries are never shared with or suggested to advertisers.
Search Ads logs pertaining to Microsoft Search are stored separately from public traffic.
Ads are never targeted to a user based on their work identity or organization.

## See also

[Set up Microsoft Search](setup-microsoft-search.md)

[Make content easy to find](make-content-easy-to-find.md)