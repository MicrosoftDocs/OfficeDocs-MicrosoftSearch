---
title: "Security for Microsoft Search"
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
description: "Protect your company's data and end users while providing information to authorized users with Microsoft Search"
---
# Security for Microsoft Search in Bing

With enterprise-grade security, Microsoft Search keeps your users and data protected.

## Secure by default

Microsoft Search in Bing requests are made over HTTPS. The connection is encrypted end-to-end for enhanced security.
  
## Authentication and authorization with Azure Active Directory

Authentication for Microsoft Search in Bing is tied to Azure Active Directory. When Microsoft Search users go to Bing, the Bing header will show sign-in options for a Microsoft account as well as a work or school account. If Bing can't determine whether a user is an eligible participant, users can go to the [Explore Microsoft Search](https://www.bing.com/business/explore) page, where they'll be automatically redirected to your organization's sign-in page.
 
Users can access Microsoft Search only through a work or school account. They need to sign in with the same credentials they use to access Office 365 services such as SharePoint or Outlook. A personal Microsoft account can't be used to sign in to Microsoft Search.
    
## Single sign-on

If a user is already authenticated with their work or school account in another service, such as Outlook or SharePoint, they'll be automatically signed into the same work or school account when they go to Bing in the same browser. Also, when the user signs out of their work or school account, they'll be automatically signed out from other Microsoft Office services in the same browser.
  
## Communicates with the Trusted Cloud from the browser

When a user signs in with their work or school account, Bing will download the necessary client libraries to the browser to enable Microsoft Search results. Then, when they search, the in-browser code calls the Office 365 cloud to get work results. To do this, Microsoft Search uses a dedicated API that is Tier C (SOC2 Type 1) compliant pursuant to the Office 365 [Compliance Framework for Industry Standards and Regulations] (https://download.microsoft.com/download/B/2/7/B27B3EF3-8849-4C18-8BA4-5AD755728620/Compliance%20Framework_customer%20guidance.pdf) (PDF download). This means work results and work data never flow through non-compliant Bing systems. 
  
## Permissions

Work results retrieved from Office 365 workloads such as SharePoint and OneDrive for Business are security trimmed at the source. Users can't see resources such as Word documents or PowerPoint presentations they can't see and access through Office 365. They can only see their own files and files that have been shared with them by the author explicitly or implicitly (through a group membership, for example) in SharePoint.

## Microsoft Search in Bing protects workplace searches

When a user enters a search query in Microsoft Search in Bing, two simultaneous search requests occur:

- A search of your organization’s internal resources.
- A separate search of public results from Bing.com.

Because workplace searches might be sensitive, Microsoft Search has implemented a set of trust measures that describe how the separate search of public results from Bing.com is handled.

### 

<Need an intro paragraph here>

- All Bing.com search logs that pertain to Microsoft Search in Bing traffic are disassociated from your workplace identity.
- If a set of restrictions or frequency thresholds are met which give us confidence that the query is not specific to a particular organization, the query will be treated as described in the Search and artificial intelligence section of the Privacy Statement (https://privacy.microsoft.com/en-US/privacystatement). For example, such queries will be used to model and train public features, such as autosuggest or related searches.
- Queries that do not meet the set of restrictions or frequency thresholds will be stored separately from public, non-Microsoft Search traffic.

### Advertising

Advertising shown on Bing.com in connection with workplace searches is solely related to the content of the search queries. Ads are never targeted to users based on their workplace identity.
     
## GDPR

The [May 21, 2018, blog post](https://blogs.microsoft.com/on-the-issues/2018/05/21/microsofts-commitment-to-gdpr-privacy-and-putting-customers-in-control-of-their-own-data/) from Microsoft reflects our commitment to GDPR compliance and how Microsoft helps businesses and organizations with their own GDPR compliance obligations. You can find additional detail in the Microsoft [Trust Center FAQ](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-faqs). 

Microsoft Search queries executed against a customer’s internal resources and results returned are considered Customer Data and, as such, also  meet the processor commitments outlined in Article 28 as reflected in the [Trust Center FAQ](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-faqs). With respect to queries from Microsoft Search that go to public Bing, Microsoft complies with its GDPR obligations as a data controller.

