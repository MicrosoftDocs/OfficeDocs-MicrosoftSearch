---
title: "FAQs"
ms.author: anfowler
author: adefowler
manager: shohara
ms.date: 10/19/2018
ms.audience: Admin
ms.topic: reference
ms.service: mssearch
localization_priority: Priority
search.appverid:
- BFB160
- MET150
- MOE150
ROBOTS: NoIndex
description: "Get answers to commonly asked questions about enterprise search and Microsoft Search"
---

# Frequently asked questions

Here's a list of the most common questions.

> [!TIP]
> Don't see your question answered here? Ask your question in this article's feedback.

## Is advanced query understanding supported?

Yes, Microsoft Search parses query intent from larger phrases. This feature uses AI to learn common superfluous phrases users add to their queries that don't impact their search intent. For example, when a user searches for 'tell me more about how to change my password please' we extract the less important words from the query and trigger based on the relevant ones like 'change password.'
  
This feature will not override keywords set in the admin center.
  
## Can you search for files on-premises?

Yes. You can search on-premises SharePoint files if you have a hybrid deployment of SharePoint.
  
## How do I make Bing the default search engine for people in my org?

Here's the instructions for setting the default search engine, default homepage, and default browser to give your users the best experience with Microsoft Search in Bing:

- [Set Edge as your default browser](set-default-browser.md)
- [Make Bing your default search engine](set-default-search-engine.md)
- [Set Bing.com as your enterprise homepage](set-default-homepage.md)

  
## How are my search results protected?

We require Azure Active Directory (AAD) authentication to access results from the Trusted Cloud. Authenticated users only see content they have access to. Search queries are de-identified and logs are separated from public Bing search traffic. This level of protection is unavailable anywhere else in the industry.

## Can I search across federated organizations?

No.

## Where can I get info about Office 365 and Microsoft 365 compliance tiers and categories?

Details can be found in the [Compliance Framework for Industry Standards and Regulations](https://download.microsoft.com/download/B/2/7/B27B3EF3-8849-4C18-8BA4-5AD755728620/Compliance%20Framework_customer%20guidance.pdf) (PDF download).

## Can users earn Microsoft Rewards points with their work account?

Microsoft Search requires a user to sign in with a work or school account, but a user cannot create or sign into the Microsoft Rewards program with that account. However, there is an instance when an enterprise user may see Rewards points accrue. This can happen when a Microsoft Search user has a Rewards account created with a <a href="https://www.microsoft.com/en-us/welcome?rtc=1">Microsoft account</a>. (You have a Microsoft account if you use an email address, Skype ID, or phone number, and a password to sign into Microsoft services like Office 365, Xbox consoles, or Windows 10 PCs. The email address you use for your Microsoft account can be from Outlook.com, Hotmail.com, Gmail, Yahoo, or other providers.) If a user has signed in alternately with both their work account and Microsoft account in the same browser session, they may accrue points to their Rewards account. The user can stop accruing points while searching with Microsoft Search by clearing their cookies.
