---
title: "Microsoft Search FAQs"
ms.author: bstucker
author: bstuck
manager: bstucker
ms.audience: Admin
ms.topic: reference
ms.service: mssearch
ms.localizationpriority: medium
ms.date: 03/15/2022
search.appverid:
- BFB160
- MET150
- MOE150
description: "Get answers to commonly asked questions about Microsoft 365 enterprise and Microsoft Search"
---
# Microsoft Search FAQs

Here's a list of the most common questions.

> [!TIP]
> Don't see your question answered here? Ask your question in this article's feedback.

## Is advanced query understanding supported?

Yes, Microsoft Search parses query intent from larger phrases. This feature uses AI to learn common superfluous phrases users add to their queries that don't affect their search intent. For example, when a user searches for *tell me more about how to change my password*, we extract the less important words from the query and trigger based on the relevant ones like *change password*.
  
This feature won't override keywords set in the [Microsoft 365 admin center](https://admin.microsoft.com).
  
## Can you search for files on-premises?

Yes. You can search on-premises [SharePoint](https://sharepoint.com/) files if you have a hybrid deployment of SharePoint.
  
## How do I make Bing the default search engine for people in my org?

These are the instructions for setting the default search engine, default homepage, and default browser to give your users the best experience with Microsoft Search in [Bing](https://Bing.com):

- [Set Microsoft Edge as your default browser](/deployedge/edge-default-browser)
- [Make Bing your default search engine](set-default-search-engine.md)
- [Set Bing.com as your enterprise homepage](set-default-homepage.md)

## How are my search results protected?

We require [Microsoft Entra ID](/azure/active-directory/) authentication to access results from the Trusted Cloud. Authenticated users only see content they have access to. When using Microsoft Search in Bing, search queries are de-identified and logs are separated from public [Bing](https://Bing.com) search traffic.

## Can I search across federated organizations?

No.

## Where can I get info about Office 365 security, compliance, and privacy?

Details can be found on the [Trust Center pages for Office 365](https://www.microsoft.com/TrustCenter/CloudServices/office365/default.aspx).

## Can guests access Microsoft Search in my organization?

Microsoft 365 enables rich collaboration with people outside of your organization through [guest access.](/microsoft-365/solutions/collaborate-with-people-outside-your-organization) These users can search for documents, sites, groups, lists, and libraries. However, guests won't get the full, personalized Microsoft Search experience and may need to use the on-page search box instead of the unified Microsoft Search box in the header.

## How do I turn Microsoft Search in Bing on or off?

For most organizations, including enterprise and education, Microsoft Search in Bing is on by default. To turn on Microsoft Search in Bing, go to the [Configurations](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/configurations) page in the Microsoft 365 admin center. Under Microsoft Search in Bing setting, choose **Change** and select **Enable Microsoft Search in Bing at your organization**. It takes up to 24 hours for this change to take effect.

If this setting is off, users won't get internal results when they search on Bing, Windows Search, or Microsoft Edge. They also won't be able to access Microsoft 365 Chat. Turning off Microsoft Search in Bing doesn't stop or prevent internal content from being added to your search index. It only disables Bing entry points to Microsoft Search. To find answers and internal results, users need to use other entry points, for example, SharePoint Online or an Office 365 app.

## What does Microsoft Search cost?

Microsoft Search is the search for your Microsoft 365 experience; there is no additional cost to search your data. Some features like [Microsoft Graph connectors](connectors-overview.md) come with quotas that are included on certain [licenses and have extra quota available for purchase](licensing.md).
