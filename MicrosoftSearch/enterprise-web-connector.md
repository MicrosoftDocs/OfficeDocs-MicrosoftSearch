---
title: "Enterprise Website connector configuration in the M365 Admin portal"
ms.author: v-pamcn
author: TrishaMc1
manager: mnirkhe
ms.date: 10/08/2019
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Priority
search.appverid:
- BFB160
- MET150
- MOE150
description: "Enterprise Website configuration in the M365 Admin portal."
---

# Enterprise Website connector configuration in the M365 Admin portal

## Overview 
The Enterprise Website connector for Microsoft Search will allow your organization to index **content from your company’s websites** that are visible to all users within your company (tenant) but not visible to people outside your company. Once you have configured the connector and synced content from the website, the end user will then be able to search for those articles from any Microsoft Search client. 

This article is intended for M365 Search administrators, or anyone who is responsible for configuring, running, and monitoring the connector. Here you can find information on what to know before configuring your connector, how to get started, and additional information regarding connector capabilities, limitations, and troubleshooting techniques.

## Things to know before configuring your connector

**Things to Know** | **Description** | **How to get this information**
--- | --- | ---
Root URL | This is root URL which will be used to initiate the crawl. This will also be used for authentication. | This is the URL of the website that you want to crawl. 
Credentials | This is used to authenticate so that the website content can be accessed. | There are two auth modes supported – basic and OAuth 2.0 with AAD. Read below separately for each. 
Basic Auth | Requires a Username and Password | Admins need to create this bot account using the M365 Admin Center. 
OAuth 2.0 with AAD | Requires tenant ID, resource ID, Client ID and Client Secret. <br></br><br></br> Read [Authorize access to Azure Active Directory web applications using the OAuth 2.0 code grant flow](https://docs.microsoft.com/en-us/azure/active-directory/develop/v1-protocols-oauth-code) for more details. Use the following values for registration:<br></br>- Name: Microsoft Search<br></br>- Redirect_URL: https://gcs.office.com/v1.0/admin/oauth/callback<br></br><br></br>
To get the values mentioned, refer to section titled *Use the authorization code to request an access token* in the URL above. The values are named tenant, resource, client_id and client_secret. | All this info is in the AAD application registration page. <br></br><br></br> Read [Quickstart: Register an application with the Microsoft identity platform](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app) for more details.
Reverse Proxy URL | Since the connector itself is cloud-based, it doesn’t have access to on-prem content. To provide access to on-prem content, the admins will need to install a reverse proxy. <br></br><br></br> A reverse proxy will be used to provide a secure, performant and reliable access to on-prem websites. The reverse proxy recommended here is [Azure Application Proxy (AAP)](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/application-proxy-security). <br></br><br></br> The requirement for root URL and authentication remains the same. The only difference is that the root URL and authentication is now provided by the reverse proxy server. | [Remote access to on-premises applications through Azure Active Directory's Application Proxy](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/application-proxy-security)
Exclusion List | The connector allows admins to exclude some URLs from getting crawled. That might be because the content is sensitive or not worth crawling. | Browse through the root URL to create the list. Once created, please add this to the exclusion list during the configuration process. 
ACLs | Access Control Lists – Controls who has access to the content. | There is no ACL support. The admin should only connect websites which are visible to any user within your tenant. 
Refresh Schedule | This connector only supports full sync. It means that every time the connector will read all the content of the website. Therefore, use a large refresh schedule to ensure the connector gets enough time to read the content. | Recommended values are between 3 days to 2 weeks. 

## Limitations
Reading dynamic webpages is not supported. Examples of where dynamic webpages live include content management systems such as Confluence or Unily, or databases configured to store website content.


