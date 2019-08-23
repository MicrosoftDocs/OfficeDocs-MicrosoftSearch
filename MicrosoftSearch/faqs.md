---
title: "FAQs"
ms.author: dawholl
author: dawholl
manager: kellis
ms.date: 10/19/2018
ms.audience: Admin
ms.topic: reference
ms.service: mssearch
localization_priority: Priority
search.appverid:
- BFB160
- MET150
- MOE150
ms.assetid: cd3ee09d-58ab-4b8a-8822-fa11a1399672
ROBOTS: NoIndex
description: "Get answers to commonly asked questions about enterprise search and Microsoft Search"
---

# Frequently asked questions

Here's a list of the most common questions.

> [!TIP]
> Don't see your question answered here? Ask your question in this article's feedback.

<<<<<<< HEAD
## Is advanced query understanding supported?
=======
Microsoft Search intelligently searches both your work and web content. This kind of integration across web and enterprise is only available with Microsoft. For compliance-related information, see [Security for Microsoft Search](security.md).
  
## What Microsoft Search features are available now?

For a complete list, see [Features of Microsoft Search](features.md).
  
## Does Microsoft Search support advanced query understanding?
>>>>>>> master

Yes, Microsoft Search parses query intent from larger phrases. This feature uses AI to learn common superfluous phrases users add to their queries that don't impact their search intent. For example, when a user searches for 'tell me more about how to change my password please' we extract the less important words from the query and trigger based on the relevant ones like 'change password.'
  
This feature will not override keywords set in the Admin portal.
  
<<<<<<< HEAD
## Can you search for files on-premises?

Yes. You can search on-premises SharePoint files if you have a hybrid deployment of SharePoint.
=======
## Does Microsoft Search search for files on-premises as well as the cloud?

Microsoft Search supports searching for documents that live on SharePoint Online, OneDrive for Business, as well as over hybrid on-premises SharePoint and SharePoint Online for the most common Office file types. If you can search on-premises content in SharePoint Online, you should be able to find on-premises content using Microsoft Search. 
  
## Does Microsoft Search replace other enterprise search experiences?

Microsoft Search is a complementary offering that brings together results from multiple sources. For more information about supported file types and sources, see the next FAQ.
  
## What file types and sources does Microsoft Search support?

We support the following content sources:
  
- SharePoint Online
    
- Hybrid SharePoint (on-premises + SPO)
    
- OneDrive for Business
    
The following file types are surfaced in file search and appear on the Files tab for People and Groups:
  
- Word
    
- Excel
    
- PowerPoint
    
- OneNote
    
- PDF
    
## What compliance and trust measures are in place for Microsoft Search?

For information about compliance and trust measures, see [Security for Microsoft Search](security.md).
  
## Where can I get info about Office 365 compliance tiers/categories?

Details can be found in the [Compliance Framework for Industry Standards and Regulations](https://download.microsoft.com/download/B/2/7/B27B3EF3-8849-4C18-8BA4-5AD755728620/Compliance%20Framework_customer%20guidance.pdf) (PDF download). 
  
## How does Microsoft Search protect search results?

For information about the safety measures in place to protect Microsoft Search keeps your results secure, see [Security for Microsoft Search](security.md).
  
## What are the content sources for the people card?

The people card derives information from Azure Active Directory, Exchange Online, and SharePoint Online.
  
## Do Microsoft Search users earn Microsoft Rewards?

Microsoft Search searches earn Rewards points if a user is signed in with their work/school account, but also has a Microsoft account (e.g., Live.com, Outlook.com, Hotmail.com) linked to Microsoft Rewards.
>>>>>>> master
  
## How do I make Bing the default search engine for people in my org?

Here's the instructions for setting the default search engine, default homepage, and default browser to give your users the best experience with Microsoft Search in Bing:

- [Set Edge as your default browser](set-default-browser.md)
- [Make Bing your default search engine](set-default-search-engine.md)
- [Set Bing.com as your enterprise homepage](set-default-homepage.md)

  
## How are search results kept secure?

We require Azure Active Directory (AAD) authentication to access results from the Trusted Cloud. Authenticated users only see content they have access to. Search queries are de-identified and logs are separated from public Bing search traffic. This level of protection is unavailable anywhere else in the industry.

## Can I search across federated organizations?

No.

## Where can I get info about Office 365 and Microsoft 365 compliance tiers and categories?

Details can be found in the [Compliance Framework for Industry Standards and Regulations](https://download.microsoft.com/download/B/2/7/B27B3EF3-8849-4C18-8BA4-5AD755728620/Compliance%20Framework_customer%20guidance.pdf) (PDF download).