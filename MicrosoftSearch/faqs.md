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

Yes, Microsoft Search parses query intent from larger phrases. This feature uses AI to learn common superfluous phrases users add to their queries that don't impact their search intent. For example, when a user searches for *tell me more about how to change my password*, we extract the less important words from the query and trigger based on the relevant ones like *change password*.
  
This feature won't override keywords set in the [Microsoft 365 admin center](https://admin.microsoft.com).
  
## Can you search for files on-premises?

Yes. You can search on-premises [SharePoint](http://sharepoint.com/) files if you have a hybrid deployment of SharePoint.
  
## How do I make Bing the default search engine for people in my org?

Here's the instructions for setting the default search engine, default homepage, and default browser to give your users the best experience with Microsoft Search in [Bing](https://Bing.com):

- [Set Microsoft Edge as your default browser](/deployedge/edge-default-browser)
- [Make Bing your default search engine](set-default-search-engine.md)
- [Set Bing.com as your enterprise homepage](set-default-homepage.md)

## How are my search results protected?

We require [Azure Active Directory](/azure/active-directory/) authentication to access results from the Trusted Cloud. Authenticated users only see content they have access to. Search queries are de-identified, and logs are separated from public [Bing](https://Bing.com) search traffic when you use Microsoft Search in Bing.

## Can I search across federated organizations?

No.

## Where can I get info about Office 365 security, compliance, and privacy?

Details can be found on the [Trust Center pages for Office 365](https://www.microsoft.com/TrustCenter/CloudServices/office365/default.aspx).

## Can guest users leverage Microsoft Search in my organization?

Microsoft 365 enables rich collaboration with people outside of your organization through [guest access.](/microsoft-365/solutions/collaborate-with-people-outside-your-organization) These users will be able to perform search operations on documents, sites, groups, lists, and libraries. However, guest users will not get the full, personalized, Microsoft Search experience and may need to leverage the on-page search box instead of the unified Microsoft Search box in the header.