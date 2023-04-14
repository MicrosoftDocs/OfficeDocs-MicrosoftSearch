--- 
title: "Release history for Microsoft Graph connector agent" 
ms.author: harshkum 
author: harshkum
manager: Siva
audience: Admin
ms.audience: Admin 
ms.topic: article 
ms.service: mssearch 
ms.localizationpriority: medium 
search.appverid: 
description: "Release history of Microsoft Graph connector agent, which is used to index the on-premises data sources using Microsoft built connectors" 
--- 

# Release history for Microsoft Graph connector agent

Indexing on-premises data sources require you to install *Microsoft Graph connector agent* software. It allows for secure data transfer between on-premises data and the connector APIs.

For help on installation, refer to this [page](graph-connector-agent.md#installation)

[Download latest Graph Connector Agent](https://aka.ms/gca)

### Version 2.1.0.0 (*10 April 2023*)

* Fix for slow crawl by optimizing local file logging
* Semantic search for Intranet connector - Parsing of HTML content to store annotations for each item to power future intelligent search capabilities
* Bug fixes and reliability improvements

### Version 2.0.1.0 (*27 Mar 2023*)

* Bug fixes and reliability improvements

### Version 2.0.0.0 (*15 Mar 2023*)

* Microsoft Graph connectors SDK GA: Updated SDK test utility with more test cases. [Learn more about Graph Connectors SDK](/graph/custom-connector-sdk-overview).
* Support for .NET 7. This requires a manual installation of the GCA and the “Upgrade” feature won't be available until this version is installed. If you're upgrading from GCA 1.x to 2.x, refer to this [page](graph-connector-agent.md).
* Improved troubleshooting of common GCA issues through "Health Check" feature in Registration details page. Now, you can click on the "Health check" button, as in the image below, to check GCA health.
:::image type="content" source="media/onprem-agent/health-check-registration.jpg" alt-text="Sample snapshot of Health check success on GCA registration page.":::

* Bug fixes and performance improvements

### Version 1.8.9.0 (*9 Feb 2023*)

* Bug fixes and reliability improvements

### Version 1.8.8.0 (*19 Jan 2023*)

* Bug fixes and reliability improvements

### Version 1.8.7.0 (*11 Jan 2023*)

* Bug fixes and reliability improvements

### Version 1.8.6.0 (*16 Dec 2022*)

* Bug fixes and reliability improvements

### Version 1.8.5.0 (*06 Dec 2022*)

* Security Enhancements
* Bug fixes and reliability improvements

### Version 1.8.2.0 (*06 Oct 2022*)

* Upgrade Graph Connector Agent with just one click in the UI. For future builds, if there are any upgrades available for Graph Connector Agent, the one-click upgrade feature will be available in the connection details pane. For older builds, there will be an option to download and install the GCA build.
![Sample snapshot of how to upgrade GCA with one-click from the connection pane.](media/gca-releases/one-click-upgrade.png)

* Bug fixes and reliability improvements

### Version 1.8.1.0 (*not supported*) (*29 Aug 2022*)

* Security Enhancements
* Bug fixes and reliability improvements

### Version 1.8.0.0 (*not supported*) (*25 Jul 2022*)

* Support for incremental crawls and OAuth for Microsoft Graph connectors SDK
* Bug fixes and reliability improvements

### Version 1.7.0.0 (*not supported*) (*16 Jun 2022*)

* Security enhancements
* Bug fixes and reliability improvements

### Version 1.6.0.0 (*not supported*) (*09 May 2022*)

* Dashboard changes to enable monitoring of multiple instances of a connector
* Bug fixes and reliability improvements

### Version 1.5.1.0 (*not supported*) (*21 Mar 2022*)

* Bug fixes and reliability improvements
* Change in default property labels assignment for 'Enterprise websites' connector

### Version 1.5.0.0 (*not supported*) (*16 Feb 2022*)

* Ability to update client-secret & certificate used for authentication 
* OAuth 2.0 support for Intranet On-premises connector 
* Support for parsing of OneNote (.one) file 
* Fixed issues in parsing word files (.doc*) & last modified date for PowerPoint files (.ppt*) 

### Version 1.4.0.0 (*not supported*) (*13 Jan 2022*)

* Support for multiple instances of a connector
* Bug fixes and reliability improvements

### Version 1.3.1.0 (*not supported*) (*28 Oct 2021*)

* File-share connectors documents per second improvements
* Other performance improvements
* Bug fixes

### Version 1.3.0.0 (*not supported*) (*8 Oct 2021*)

* General reliability improvements
* Bug fixes

### Version 1.2.1.0 (*not supported*) (*3 Sept 2021*)

* Bug fixes

### Version 1.2.0.0 (*not supported*) (*16 Aug 2021*)

* Support for localized strings in 33 languages: English - US, Arabic, Bulgarian, Catalan, Czech, Danish, German, Greek, Spanish, Estonian, Finnish, Hebrew, Croatian, Hungarian, Italian, Japanese, Korean, Lithuanian, Latvian, Dutch, Norwegian, Polish, Portuguese, Russian, Slovak, Slovenian, Serbian (Latin), Swedish, Thai, Turkish, Ukrainian, Chinese - China, Chinese - Taiwan
* Resumption of full crawl if there was an agent crash
* Bug fixes

### Version 1.1.0.0 (*not supported*) (*9 July 2021*)

* Support for Exclusions rules for file-share connector
* Performance improvements
* Bug fixes
