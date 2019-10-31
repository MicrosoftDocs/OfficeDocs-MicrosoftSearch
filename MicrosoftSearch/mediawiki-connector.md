---
title: "MediaWiki connector configuration in the M365 Admin portal"
ms.author: v-pamcn
author: monaray
manager: mnirkhe
ms.date: 11/04/2019
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "MediaWiki connector configuration in the M365 Admin portal."
---

# Configure a MediaWiki connector in Microsoft 365

With the MediaWiki connector for Microsoft Search, your organization can discover and index data from a wiki created by using MediaWiki software. This connector indexes specified content into Microsoft Search and supports periodic crawls to keep the index up to date.

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors a MediaWiki connector for Microsoft Search. It explains how to configure your connector and connector capabilities, limitations, and troubleshooting techniques.

## Connect to a data source
Enter your MediaWiki URL and credentials for authenticating the connection.

![](media/mediawiki-auth.png)

## Manage the search schema
After successful connection, configure the search schema mapping. You can choose which properties to make **queryable**, **searchable**, and **retrievable**.

## Manage search permissions
The MediaWiki connector only supports search permissions visible to **Everyone**. Indexed data appears in the search results and is visible to all users in the organization.

## Set the refresh schedule 
This schedule refreshes indexed data, so changes to the wiki are reflected in Microsoft Search. All new pages, deleted pages, page content, or metadata changes appear in search results after the specified refresh interval. The crawl time is dependent on the size of the wiki. Currently the connector crawls at around 50 pages per minute.

## Limitations 
The MediaWiki connector has these limitations in the preview release:
* Supports only cloud-based wikis.
* Supports only Basic or OAuth 2.0 with Azure Active Directory or Azure authentication.
* Doesn't support namespace selection for indexing. Indexes only **Main**, **Category**, and **File** namespaces.
* Doesn't support Access Control Lists (ACLs). Thus, indexed pages are visible to all users in the organization.
