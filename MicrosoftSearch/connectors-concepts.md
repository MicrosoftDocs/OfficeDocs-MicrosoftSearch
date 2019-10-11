---
title: "Connectors Concepts"
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
description: "concepts about connectors"
---

# Connectors Concepts

### High-level architecture
{ INSERT GRAPHIC HERE = what does the graphic look like for MS-built connectors vs partner vs build your own? } 

### Definitions

*Data source*
The data source is the third-party data you want to be indexed and stored in the Microsoft Search index. The data source can either live on-premises or in the cloud.

*Connection*
A connection to a data source entails proper access to the data (authentication), traversal of the document repository, and feeding of the data to the graph connector service for indexing. 

*Search schema*
The search schema is a set of search attributes associated with the set of managed properties—these attributes enable search functionalities of the different properties and help determine what results are displayed on the search results page and what results are searchable from the end user experience. The following attributes are supported and enable the following functionalities:

**Managed Property Setting** | **What it does** | **Example**
--- | --- | ---
*Searchable* | Enables the text content of the property to be searched for. The content of this property is included in the full-text index. | If the property is “Title,” a query for “Enterprise” returns items that contain the word “Enterprise” and items with “Enterprise” in the title
*Queryable* | Enables searching for a match for that particular property. The property name must be specified in the query either programmatically or verbatim. | If the property is “Title,” a query must contain “Title: Enterprise.”
*Retrievable* | Enables the content of this property to be displayed in the search results. | 

*Custom search application*
A software application built on top of Microsoft Graph APIs that enables custom search capabilities and custom search interfaces. Customizable search capabilities include search rankings, filtering results, and data source reporting. Learn how to build your own application experience on top of M365 and third-party data here. 
( INSERT LINKS ABOVE ) ^^^

*Search user interface*
The user interface (UI) used by your employees or customers to search content from your Microsoft Search application. Learn how to customize your search UI by creating your verticals and modern result types here.
( INSERT LINKS ABOVE ) ^^^

