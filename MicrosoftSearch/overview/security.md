---
title: "Security for Microsoft Search"
ms.author: anfowler
author: anfowler
manager: mnirkhe
ms.date: 9/12/2018
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
ms.assetid: 50461cb9-8707-46c1-935a-1b9608a98800
description: "Protect your enterprise data and users while providing information to authorized users with Microsoft Search in Bing"
---

# Security for Microsoft Search

With enterprise-grade security, Microsoft Search in Bing always keeps your users and data protected.
  
## Secure by default

Microsoft Search in Bing always ensures requests are made over HTTPS. This safeguard ensures the connection is encrypted end-to-end for enhanced security.
  
## Authentication and authorization with Azure Active Directory

Authentication for Microsoft Search in Bing is tied to Azure Active Directory. For eligible Microsoft Search in Bing users, the Bing header will show sign-in options for a Microsoft account as well as a work or school account. If Bing can't determine whether a user is an eligible participant, users can go to the [Explore Microsoft Search in Bing](https://go.microsoft.com/fwlink/?linkid=2017806) page, where they'll be automatically redirected to your organization's sign-in page. 
  
Users can access Microsoft Search in Bing only through a work or school account. They need to sign in with the same credentials they use to access Office 365 services such as SharePoint or Outlook. A personal Microsoft account can't be used to sign in to Microsoft Search in Bing.
  
Users can't be signed in to Bing with both a Microsoft account and a work or school account at the same time.
  
## Single sign-on

If a user is already authenticated with their work or school account in another service, such as Outlook or SharePoint, they'll be automatically signed in to Microsoft Search in Bing when they go to Bing in the same browser. Also, when the user signs out of Microsoft Search in Bing, they'll be automatically signed out from other services in the same browser.
  
## Communicates with the Trusted Cloud from the browser

When a user signs in with their work or school account, Bing will download the necessary client libraries to the browser to enable Microsoft Search in Bing results. Then, when they search, the in-browser code calls the Office 365 cloud to get work results. To do this, Microsoft Search in Bing uses a dedicated API that is Tier C (SOC2 Type 1) compliant pursuant to the Office 365 [Compliance Framework for Industry Standards and Regulations](https://go.microsoft.com/fwlink/?linkid=2019579) (PDF download). This means work results and work data never flow through non-compliant Bing systems. 
  
## Permissions

Work results retrieved from Office 365 workloads such as SharePoint and OneDrive for Business are security trimmed at the source. Users can't see resources such as Word documents or PowerPoint presentations they can't see and access through Office 365. They can only see their own files and files that have been shared with them by the author explicitly or implicitly (through a group membership, for example) in SharePoint.
  
## Protects user queries from the public portion of Bing

Because work-related searches may be sensitive, Microsoft Search in Bing has implemented a set of trust measures for how these are handled by the public web results part of Bing.
  
Regardless of whether a user query contains one or more work results in the returned response, the following measures are taken:
  
- Logging
    
  - All search logs pertaining to Microsoft Search in Bing traffic are de-identified and stored separately from public, non-Microsoft Search in Bing traffic. They're retained for 18 months, and access is restricted for debugging purposes only.
    
  - The queries in these logs are not used to model or train public features such as autosuggest or related searches for the public web.
    
  - Restricted access is managed via various secure mechanisms, including security groups and other layers within the engineering system.
    
- Search history
    
  - When signed in with a work or school account, a user's search history won't be available on other computers or devices.
    
- Advertising
    
  - Enterprise search queries are never shared with or suggested to advertisers.
    
  - Search Ads logs pertaining to Microsoft Search in Bing are stored separately from public traffic.
    
  - Ads are never targeted to a user based on their work identity or organization.
    
## GDPR

The [May 21, 2018, blog post](https://go.microsoft.com/fwlink/?linkid=2019071) from Microsoft reflects our commitment to GDPR compliance and how Microsoft helps businesses and organizations with their own GDPR compliance obligations. You can find additional detail in the Microsoft [Trust Center FAQ](https://go.microsoft.com/fwlink/?linkid=2019074). Microsoft Search in Bing queries that operate against organizational customers' Customer Data within the Online Services will also meet the processor commitments outlined in Article 28 as reflected in the [Trust Center FAQ](https://go.microsoft.com/fwlink/?linkid=2019074). With respect to queries from Microsoft Search in Bing that go to public Bing, Microsoft is a data controller and has implemented measures to de-identify the queries as outlined under GDPR.
  
## See also

[Why Microsoft Search in Bing](why-microsoft-search.md)
  
[Features of Microsoft Search in Bing](features.md)
  
[Administering Microsoft Search in Bing](https://support.office.com/article/58cb3d89-b46c-45c1-91a2-21b81c1f0c33.aspx)
  

