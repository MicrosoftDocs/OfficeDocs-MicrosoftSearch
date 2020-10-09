---
title: "FAQs"
ms.author: jeffkizn
author: jeffkizn
manager: parulm
ms.audience: Admin
ms.topic: reference
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Get answers to commonly asked questions about enterprise search and Microsoft Search"
---
<!-- markdownlint-disable no-trailing-punctuation -->
# Frequently asked questions

Here's a list of the most common questions.

> [!TIP]
> Don't see your question answered here? Ask your question in this article's feedback.

## Is advanced query understanding supported?

Yes, Microsoft Search parses query intent from larger phrases. This feature uses AI to learn common superfluous phrases users add to their queries that don't impact their search intent. For example, when a user searches for *tell me more about how to change my password please*, we extract the less important words from the query and trigger based on the relevant ones like *change password*.
  
This feature won't override keywords set in the [Microsoft 365 admin center](https://admin.microsoft.com).
  
## Can you search for files on-premises?

Yes. You can search on-premises [SharePoint](http://sharepoint.com/) files if you have a hybrid deployment of SharePoint.
  
## How do I make Bing the default search engine for people in my org?

Here's the instructions for setting the default search engine, default homepage, and default browser to give your users the best experience with Microsoft Search in [Bing](https://Bing.com):

- [Set Microsoft Edge as your default browser](set-default-browser.md)
- [Make Bing your default search engine](set-default-search-engine.md)
- [Set Bing.com as your enterprise homepage](set-default-homepage.md)

## How are my search results protected?

We require [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/) authentication to access results from the Trusted Cloud. Authenticated users only see content they have access to. Search queries are de-identified, and logs are separated from public [Bing](https://Bing.com) search traffic. This level of protection is unavailable anywhere else in the industry.

## Can I search across federated organizations?

No.

## Where can I get info about Office 365 security, compliance, and privacy?

Details can be found on the [Trust Center pages for Office 365](https://www.microsoft.com/TrustCenter/CloudServices/office365/default.aspx).

## Can users earn Microsoft Rewards points with their work or school account?

Microsoft Search requires that enterprise users sign in with a work or school account. But users can’t join or sign in to the Microsoft Rewards program with those accounts. However, there is an instance when an enterprise user may see Rewards points accrue. This can happen when a Microsoft Search user has a Rewards account that was created with a [Microsoft account](https://www.microsoft.com/welcome?rtc=1). (The email address associated with a Microsoft account can be from Outlook.com, Hotmail.com, Gmail, Yahoo, or other providers.) If users sign in alternately with both their work account and Microsoft account in the same browser session, they might accrue points to their Rewards account. Users can stop accruing points while searching with Microsoft Search by clearing their cookies.

## Can guest users leverage Microsoft Search in my organization?

Microsoft 365 enables rich collaboration with people outside of your organization through [guest access.](https://docs.microsoft.com/microsoft-365/solutions/collaborate-with-people-outside-your-organization?view=o365-worldwide) These users will be able to perform search operations on documents, sites, groups, lists, and libraries. However, guest users will not get the full, personalized, Microsoft Search experience and may need to leverage the on-page search box instead of the unified Microsoft Search box in the header.
