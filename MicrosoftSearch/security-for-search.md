---
title: "Security and Privacy for Microsoft Search in Bing"
ms.author: kellis
author: kellis
manager: makers
ms.audience: Admin
ms.topic: concept-article
ms.service: mssearch
ms.localizationpriority: medium
ms.collection: essentials-security
search.appverid:
- BFB160
- MET150
- MOE150
description: "Protect your company's data and end users while providing information to authorized users with Microsoft Search in Bing"
ms.date: 12/10/2019
---

# Security and Privacy for Microsoft Search in Bing

With enhanced privacy and security measures, Microsoft Search in Bing helps protect your users and workplace data.

## Secure by default

Microsoft Search in Bing requests are made over HTTPS. The connection is encrypted end-to-end for enhanced security.
  
<a name='authentication-and-authorization-with-azure-active-directory'></a>

## Authentication and authorization with Microsoft Entra ID

Authentication for Microsoft Search in Bing is tied to Microsoft Entra ID. When Microsoft Search users go to Bing, the Bing header shows sign-in options for a Microsoft account and a work or school account. If Bing can't determine whether a user is an eligible participant, users can go to the [Explore Microsoft Search](https://www.bing.com/business/explore) page, where they are automatically redirected to your organization's sign-in page.

Users can access Microsoft Search only through a work or school account. They need to sign in with the same credentials they use to access Office 365 services such as SharePoint or Outlook. A personal Microsoft account can't be used to sign in to Microsoft Search.

## Single sign-on

If a user is already authenticated with their work or school account in another service, such as Outlook or SharePoint, they are automatically signed into the same work or school account when they go to Bing in the same browser. Also, when the user signs out of their work or school account, they are automatically signed out from other Microsoft Office services in the same browser.
  
## Communicates with the Microsoft cloud from the browser

When a user signs in with their work or school account, Bing downloads the necessary client libraries to the browser to enable Microsoft Search results. Then, when they search, the in-browser code calls the Office 365 cloud to get work results. To do this, Microsoft Search uses a dedicated API that is operated in accordance with the control objectives of SSAE 18 SOC2 Type 1. This means work results and work data don't flow through Bing systems that are subject to less stringent data processing control objectives than the work results themselves are subject to when processed in Office 365 Core Online Services.
  
## Permissions

Work results retrieved from Office 365 workloads such as SharePoint and OneDrive for Business are security trimmed at the source. Users can't see resources such as Word documents or PowerPoint presentations they can't see and access through Office 365. They can only see their own files and files that have been shared with them by the author explicitly or implicitly (through a group membership, for example) in SharePoint.

## Microsoft Search in Bing protects workplace searches

When a user enters a search query in Microsoft Search in Bing, two simultaneous search requests occur:

- A search of your organization’s internal resources.
- A separate search of public results from Bing.com.

Because workplace searches might be sensitive, Microsoft Search has implemented a set of trust measures that describe how the separate search of public results from Bing.com is handled.

### Logging

- All Bing.com search logs that pertain to Microsoft Search in Bing traffic are disassociated from your workplace identity.
- If a set of restrictions or frequency thresholds are met which give us confidence that the query isn't specific to a particular organization, the query is treated as described in the Search and artificial intelligence section of the [Privacy Statement](https://privacy.microsoft.com/privacystatement). For example, such queries are used to model and train public features, such as autosuggest or related searches.
- Queries that don't meet the set of restrictions or frequency thresholds are stored separately from public, non-Microsoft Search traffic.

### Advertising

Advertising shown on Bing.com with workplace searches is solely related to the content of the search queries. Ads are never targeted to users based on their workplace identity.

## GDPR

The [May 21, 2018, blog post](https://blogs.microsoft.com/on-the-issues/2018/05/21/microsofts-commitment-to-gdpr-privacy-and-putting-customers-in-control-of-their-own-data/) from Microsoft reflects our commitment to GDPR compliance and how Microsoft helps businesses and organizations with their own GDPR compliance obligations. You can find more details in the Microsoft [Trust Center FAQ](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-faqs).

Microsoft Search queries executed against a customer’s internal resources and results returned are considered Customer Data and, as such, also  meet the processor commitments outlined in Article 28 as reflected in the [Trust Center FAQ](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-faqs). With respect to queries from Microsoft Search that go to public Bing, Microsoft complies with its GDPR obligations as a data controller.
