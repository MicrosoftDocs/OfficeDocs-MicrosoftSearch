---
title: "MediaWiki connector configuration in the M365 Admin portal"
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
description: "MediaWiki connector configuration in the M365 Admin portal."
---

# MediaWiki connector configuration in the M365 Admin portal

## Overview
The MediaWiki connector for Microsoft Search will allow your organization to discover and index data from a Wiki created using MediaWiki software. Connector will ingest the specified content into the Microsoft search index and support periodic crawls to keep the index up to date. 
 
This article is intended for Microsoft 365 Search administrators, or anyone who is responsible for configuring, running, and monitoring the connector. Here you can find information on what to know before configuring your connector, how to get started, and additional information regarding connector capabilities, limitations, and troubleshooting techniques.

## Things to know before configuring your connector

### Capabilities 
* Indexes wikis based on MediaWiki by creating ‘connections’ through the Microsoft 365 Amin Center 
* Full crawl to index the pages on creating connection, periodic incremental crawl to pick updates 
* Search through indexed content in Sharepoint, Bing search, Office.com 
* Search through page title, description, content and other data and metadata 
* Edit or create your own result layout (MRT) 
* Check status of connection; edit name, description; delete connection 

### Limitations  
* Currently only cloud-based wikis are supported 
* Currently only Basic or OAuth 2.0 with AAD/Azure authentications are supported. 
* Currently namespaces cannot be selected for indexing; Main, Category and File namespaces will be indexed; Other namespaces will not be indexed 
* Access Control Lists are not supported for MediaWiki connector, indexed pages will be visible to everyone in the organization 

## Connect to data source
Enter your MediaWiki URL and credentials for authenticating the connection.

# Map to Search Schema


## Troubleshooting 
If the vertical not showing up on Sharepoint SERP after configuring, then the following problems may exist:
1. The vertical is not enabled – click on vertical and select ‘Enable’ to enable the vertical 
2. The cache is not updated. Visit SharePoint.com and enter a search query to go to search results page. Here, append **&cacheClear=true** to the URL to clear the cache and see recently created verticals.