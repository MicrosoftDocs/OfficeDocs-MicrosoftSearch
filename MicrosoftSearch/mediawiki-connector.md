---
title: "MediaWiki connector for Microsoft Search"
ms.author: monaray
author: monaray97
manager: mnirkhe
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Set up the MediaWiki connector for Microsoft Search"
---

# MediaWiki connector

With the MediaWiki connector, your organization can discover and index data from a wiki created by using MediaWiki software. This connector indexes specified content into Microsoft Search and supports periodic crawls to keep the index up to date.

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors a MediaWiki connector. It explains how to configure your connector and connector capabilities, limitations, and troubleshooting techniques.

## Connect to a data source

Enter your MediaWiki URL and credentials for authenticating the connection. You'll need the following information: **Tenant ID**, **Resource ID**, **Client ID**, and the **Client Secret**.

## Manage search permissions

The MediaWiki connector only supports search permissions visible to **Everyone**. Indexed data appears in the search results and is visible to all users in the organization.

## Manage schema

On the **Manage Schema** screen, you have the option to change the schema attributes (**queryable**, **searchable**, and **retrievable**) associated with the properties. See [Search schema attributes](https://docs.microsoft.com/en-us/microsoftsearch/configure-connector#search-schema-attributes) to learn more.

## Set the refresh schedule

This schedule refreshes indexed data, so changes to the wiki are reflected in Microsoft Search. All new pages, deleted pages, page content, or metadata changes appear in search results after the specified refresh interval. The crawl time is dependent on the size of the wiki. Currently the connector crawls at around 50 pages per minute.

## Limitations

The MediaWiki connector has these limitations in the preview release:

* Supports only cloud-based wikis.
* Supports only Basic or OAuth 2.0 with Azure Active Directory or Azure authentication.
* Doesn't support namespace selection for indexing. Indexes only **Main**, **Category**, and **File** namespaces.
* Doesn't support Access Control Lists (ACLs). Thus, indexed pages are visible to all users in the organization.
