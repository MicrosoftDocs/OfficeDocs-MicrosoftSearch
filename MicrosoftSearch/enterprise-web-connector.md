---
title: "Enterprise Websites connector for Microsoft Search"
ms.author: mounika.narayanan
author: monaray
manager: mnirkhe
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Set up the Enterprise websites connector for Microsoft Search"
---

# Enterprise websites connector

With the Enterprise websites connector, your organization can index articles and **content from its internal-facing websites**. After you configure the connector and sync content from the website, end users can search for that content from any Microsoft Search client.

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors an Enterprise websites connector. It explains how to configure your connector and connector capabilities, limitations, and troubleshooting techniques.  

## Connect to a data source 
To connect to your data source, you need your root URL and a form of authentication (Basic Authentication or OAuth 2.0 with Azure AD).

### Root URL
The root URL is what initiates the crawl and is used for authentication. You can get the URL from the home page of the website you want to crawl.

### Authentication 
Basic Authentication requires a username and password. Create this bot account by using the [Microsoft 365 admin center](https://admin.microsoft.com).

OAuth 2.0 with Azure AD requires a tenant ID, resource ID, Client ID, and Client Secret.
For more information, see [Authorize access to Azure Active Directory web applications using OAuth 2.0 code grant flow](https://docs.microsoft.com/azure/active-directory/develop/v1-protocols-oauth-code). Register with the following values:
* **Name:** Microsoft Search
* **Redirect_URI:** `https://gcs.office.com/v1.0/admin/oauth/callback`

To get the values for named tenant, resource, client_id, and client_secret, go to **Use the authorization code to request an access token** on the redirect URL webpage.

For even more information, see [Quickstart: Register an application with the Microsoft identity platform](https://docs.microsoft.com/azure/active-directory/develop/quickstart-register-app).

### Reverse proxy URL 
The Enterprise websites connector is cloud-based, so it doesn't access on-premises content. To provide that access, install a reverse proxy. A reverse proxy provides secure, reliable access to on-premises websites. We recommend Azure Application Proxy (AAP).

The reverse proxy requirement for root URL and authentication is the same as for cloud-based content except that the root URL and authentication are provided by the reverse proxy server.

See [Security considerations for accessing apps remotely with Azure AD Application Proxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-security).

## Select the source properties 
Source properties are defined based on the data format of the enterprise website. However you can create an **Exclusion list** to exclude some URLs from getting crawled since that content might be sensitive or not worth crawling. To create an exclusion list, browse through the root URL. You have the option to add the excluded URLs to the list during the configuration process.

## Manage search permissions 
There is no support for Access Control Lists (ACLs). Thus, it is advised to connect only the websites that are visible to any user within your organization.

## Set the refresh schedule
The Enterprise websites connector only supports a full crawl. This means that the connector reads all the website's content during every crawl. To make sure the connector gets enough time to read the content, it is recommended to set a large refresh schedule interval. We recommend a scheduled refresh between three days and two weeks.

## Limitations 
The Enterprise websites connector doesn't support searching data on dynamic webpages. Examples of those webpages live in content management systems like Confluence and Unily or databases that store website content.