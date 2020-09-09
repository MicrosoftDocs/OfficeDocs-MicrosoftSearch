---
title: "Enterprise Websites connector for Microsoft Search"
ms.author: monaray
author: monaray97    
manager: jameslau
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
<!-- markdownlint-disable no-inline-html -->
# Enterprise websites connector

With the Enterprise websites connector, your organization can index articles and **content from its internal-facing websites**. After you configure the connector and sync content from the website, end users can search for that content from any Microsoft Search client.

This article is for [Microsoft 365](https://www.microsoft.com/microsoft-365) administrators or anyone who configures, runs, and monitors an Enterprise websites connector. It explains how to configure your connector and connector capabilities, limitations, and troubleshooting techniques.  

## Connect to a data source

To connect to your data source, you need your root URL and a form of authentication: None, Basic Authentication, or OAuth 2.0 with [Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/).

### Authentication

Basic Authentication requires a username and password. Create this bot account by using the [Microsoft 365 admin center](https://admin.microsoft.com).

OAuth 2.0 with [Azure AD](https://docs.microsoft.com/azure/active-directory/) requires a resource ID, Client ID, and Client Secret.

For more information, see [Authorize access to Azure Active Directory web applications using OAuth 2.0 code grant flow](https://docs.microsoft.com/azure/active-directory/develop/v1-protocols-oauth-code). Register with the following values:

**Name:** Microsoft Search <br/>
**Redirect_URI:** `https://gcs.office.com/v1.0/admin/oauth/callback`

To get the values for the resource, client_id, and client_secret, go to **Use the authorization code to request an access token** on the redirect URL webpage.

For even more information, see [Quickstart: Register an application with the Microsoft identity platform](https://docs.microsoft.com/azure/active-directory/develop/quickstart-register-app).

### Root URL

The root URL is what initiates the crawl and is used for authentication. You can get the URL from the home page of the website you want to crawl.

## Select the source properties

Source properties are defined based on the data format of the enterprise website. However, you can create an **Exclusion list** to exclude some URLs from getting crawled if that content is sensitive or not worth crawling. To create an exclusion list, browse through the root URL. You have the option to add the excluded URLs to the list during the configuration process.

## Manage search permissions

There's no support for Access Control Lists (ACLs). Thus, we recommend connecting only the websites that are visible to any user within your organization.

## Set the refresh schedule

The Enterprise websites connector only supports a full crawl. This means that the connector reads all the website's content during every crawl. To make sure the connector gets enough time to read the content, we recommend that you set a large refresh schedule interval. We recommend a scheduled refresh between one and two weeks.

## Troubleshooting

When reading the website's content, the crawl may encounter some source errors which are represented by the detailed error codes below. To get more information on the types of errors, go to the **error details** page after selecting the connection. Click on the **error code** to see more detailed errors. Also refer to [Manage your connector](https://docs.microsoft.com/microsoftsearch/manage-connector) to learn more.

 Detailed Error code | Error message
 --- | ---
 6001 | The site that is being tried to index is not reachable
 6005 | The source page that is being tried to index has been blocked by as per robots.txt configuration.
 6008 | Unable to resolve the DNS
 6009 | For all client side errors (Except HTTP 404, 408), please refer to HTTP 4xx error codes for details.
 6013 | The source page that is being tried to index could not be found. (HTTP 404 error)
 6018 | The source page is not responding, and the request has timed out. (HTTP 408 error)
 6021 | The source page that is being tried to index has no textual content on the page.
 6023 | The source page that is being tried to index is unsupported (not a HTML page)
 6024 | The source page that is being tried to index has unsupported content.

* Errors 6001-6013 occur when the data source is not reachable due to a network issue or when the data source itself is deleted, moved, or renamed. Check if the data source details provided are still valid.
* Errors 6021-6024 error occur when the data source contains non-textual content on the page or when the page is not an HTML. Please check the data source and add this page in exclusion list or ignore the error.

## Limitations

The Enterprise websites connector doesn't support searching data on **dynamic webpages**. Examples of those webpages live in content management systems like [Confluence](https://www.atlassian.com/software/confluence) and [Unily](https://www.unily.com/) or databases that store website content.
