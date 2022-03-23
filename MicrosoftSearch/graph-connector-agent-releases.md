--- 
title: "Graph Connector Agent release history" 
ms.author: harshkum 
author: harshkum
manager: Siva
audience: Admin
ms.audience: Admin 
ms.topic: article 
ms.service: mssearch 
ms.localizationpriority: medium 
search.appverid: 
description: "Release history of Graph Connector Agent, which is used to index the on-premises data sources using Microsoft built Graph connectors" 
--- 

# Release history for Microsoft Graph connector agent

Indexing on-prem data sources require you to install *Microsoft Graph connector agent* software. It allows for secure data transfer between on-premises data and the connector APIs. For help on installation, please refer to this [page](graph-connector-agent.md#installation)

[Download latest Graph Connector Agent](https://aka.ms/gcadownload)

### [Version 1.5.0.0](https://aka.ms/gcadownload) (*16 Feb, 2022*)
* Ability to update client-secret & certificate and used for authentication 
* OAuth 2.0 support for Intranet On-premises connector 
* Support for parsing of OneNote (.one) file 
* Fixed issues in parsing word files (.doc*) & last modified date for PowerPoint files (.ppt*) 

### Version 1.4.0.0 (*13 Jan, 2022*)
* Bug fixes
* General reliability improvements

### Version 1.3.1.0 (*28 Oct, 2021*)
* File-share connectors documents per second improvements
* Other performance improvements
* Bug fixes

### Version 1.3.0.0 (*8 Oct, 2021*)
* General reliability improvements
* Bug fixes

### Version 1.2.1.0 (*not supported*) (*3 Sept, 2021*)
* Bug fixes

### Version 1.2.0.0 (*not supported*) (*16 Aug, 2021*)
* Support for localized strings in 33 languages: English US, Arabic, Bulgarian, Catalan, Czech, Danish, German, Greek, Spanish, Estonian, Finnish, Hebrew, Croatian, Hungarian, Italian, Japanese, Korean, Lithuanian, Latvian, Dutch, Norwegian, Polish, Portuguese, Russian, Slovak, Slovenian, Serbian (Latin), Swedish, Thai, Turkish, Ukrainian, Chinese - China, Chinese - Taiwan
* Resumption of full crawl if there was an agent crash
* Bug fixes

### Version 1.1.0.0 (*not supported*) (*9 July, 2021*)
* Support for Exclusions rules for file-share connector
* Performance improvements
* Bug fixes
