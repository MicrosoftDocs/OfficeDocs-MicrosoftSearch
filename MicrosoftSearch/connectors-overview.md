---
title: "Microsoft Graph Connectors Overview"
ms.author: mecampos
author: mecampos
manager: umas
audience: Admin
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Overview of Microsoft Graph connectors for Microsoft Search"
---
<!---Previous ms.author: monaray --->

# Overview of Microsoft Graph connectors

[Microsoft Search](./overview-microsoft-search.md) indexes all your [Microsoft 365](https://www.microsoft.com/microsoft-365) data to make it searchable for users. With Microsoft Graph connectors, your organization can index third-party data so it appears in Microsoft Search results. This feature expands the types of content sources that are searchable in your Microsoft 365 productivity apps and the broader Microsoft ecosystem. The third-party data can be hosted on-premises or in the public or private clouds.

<!---link Microsoft Graph reference in line 19 when we have access to relevant documentation--->

This article is intended to help Microsoft 365 administrators locate the resources that are available to answer the following questions:

* [What data sources can be connected to Microsoft Search?](#what-data-sources-can-be-connected-to-microsoft-search)
* [How do I manage my connections?](#how-do-i-manage-my-connections)
* [What are the license requirements and terms of use for Graph connectors?](#what-are-the-license-requirements-and-terms-of-use-for-graph-connectors)
* [What are the preview features?](#what-are-the-preview-features)
* [How do I customize and configure search results?](#how-do-i-customize-and-configure-search-results)
* [How do I search my connector data from a custom application?](#how-do-i-search-my-connector-data-from-a-custom-application)
* [How do I customize search results?](#how-do-i-customize-search-results)
* [What are the connector limitations](#what-are-the-connector-limitations)

<!---Modify to another note that is more accurate after rollout completion--->
> [!IMPORTANT]
> Microsoft Graph connectors and Microsoft Search APIs are now generally available. The first rollouts will be to customers configured for  targeted release. If you want to use a Graph connector in your tenant, users and administrators must opt into [Targeted release](/microsoft-365/admin/manage/release-options-in-office-365?preserve-view=true&view=o365-worldwide).

<!---Add Value, scenario, example, and/or graphic in December updates--->
<!---Probably remove architecture section below
## Architecture

The following architectural diagram of the Microsoft Graph platform shows how Graph connector content flows through content indexing to user results in [Microsoft Search](./overview-microsoft-search.md) clients. The rest of this section explains each of the key building blocks in the diagram.

![Diagram: on-premises and cloud-based data is pulled by connectors and indexed by the Microsoft Search API, and then the Microsoft Search service delivers the results to users.](media/connectors-overview/highlevel-connectors.png)
Graph connectors can pull data from cloud-based (SaaS) data sources and on-premises data stores. The above diagram shows connections to only two data sources, but you can add connections to up ten sources per tenant.

The Microsoft Graph Connectors API instantiates one connection per data source. Then, the API indexes and stores the data. Established connections interact with Microsoft Search, so users can get search results.

You can use the Microsoft 365 [admin center](https://admin.microsoft.com) to setup and manage any of the Graph connectors by Microsoft. The admin center has a simple user interface that makes it easy to establish the connection to your data source, and monitor connection status and utilization.

***Edit paragraph below***
To create a **connection** to a data source, admins need authenticated access to the data and the entire content repository. The data is fed to the graph connector service for indexing.--->

## What data sources can be connected to Microsoft Search?

Microsoft provides 9 Graph connectors and our ecosystem partners have created over 100 more Graph connectors. You can also build your own Graph connector.

### Graph connectors by Microsoft

You can connect to the following data sources using Graph connectors created by Microsoft:

<!---Add links below when new docs are created--->
* [Azure Data Lake Storage Gen2](azure-data-lake-connector.md)
* [Azure DevOps](azure-devops-connector.md)
* [Azure SQL and Microsoft SQL Server](MSSQL-connector.md)
* [Enterprise websites](enterprise-web-connector.md)
* [MediaWiki](mediawiki-connector.md)
* [File share](fileshare-connector.md)
* [Oracle SQL (preview)](OracleSQL-connector.md)
* [Salesforce (preview)](salesforce-connector.md)
* [ServiceNow](servicenow-connector.md)

The [Graph connectors gallery](connectors-gallery.md) contains a brief description of each of these Graph connectors. If you're ready to connect one of these data sources to your tenant, be sure to read the [Setup overview](configure-connector.md) and any other articles in the Setup connectors by Microsoft section that apply to your data source.

### Graph connectors by our partners

The [Microsoft Graph connectors gallery](connectors-gallery.md) includes a brief description of each of the Graph connectors created by our partners, and a link to each partner's website. To learn more, contact each partner directly.

### Build your own Graph connector

You can build your own Graph connector if you prefer. For more information on building Graph connectors, see the [Overview of the Microsoft Search API in Microsoft Graph](/graph/search-concept-overview).

## How do I manage my connections?

You can manage your connections from the [Connectors tab](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/Connectors) in the [Microsoft 365 admin center](https://admin.microsoft.com/). For more information about managing connections, see: [Manage your connections](manage-connector.md).

## What are the license requirements and terms of use for Graph connectors?

You need a valid Microsoft 365 or Office 365 license and sufficient Graph Connectors quota for users in your organization to view data from connectors in their search results.

To learn more, see [License requirements and pricing](licensing.md) and [Terms of use](terms-of-use.md).

## What are the preview features?

Although Microsoft Graph connectors and Microsoft Search APIs are now generally available, there are several features that are in preview.

The set of connectors and features in preview include:

* [Azure DevOps connector](azure-devops-connector.md)
* [Salesforce connector](salesforce-connector.md)
* [ServiceNow connector](servicenow-connector.md) with search permissions that use source ACLs
* [Manage result cluster](result-cluster.md)
* [Multiple connections under a vertical](multiple-connections-in-a-vertical.md)

## How do I customize and configure search results?

There are many ways to customize and configure search results. See the following articles to learn more:

* [Manage verticals and result types](customize-search-page.md)
* [Manage search result layouts](customize-results-layout.md)
* [Manage result cluster](result-cluster.md)
* [Manage custom filters](custom-filters.md)

## How do I search my connector data from a custom application?

After custom data is indexed, developers can [query this data](/graph/search-concept-custom-types). You can view your data in any application. For more information, see the [Overview of the Microsoft Search API in Microsoft Graph](/graph/search-concept-overview).

## How do I customize search results?

The next step is to customize the search results as recommended in this article [How do I customize and configure search results?](#how-do-i-customize-and-configure-search-results). To learn more about customizing search results, see [Customize the search results page](customize-search-page.md).

## What are the connector limitations?

* When you **publish** a Microsoft-built connector, it might take a few minutes for the connection to be created. During that time, the connection will show its status as pending.

* The [Microsoft 365 admin center](https://admin.microsoft.com) doesn't support editing the **search schema** after a connection is published. To edit the search schema, delete your connection and then create a new one.

* Ingestion throughput is throttled at about four items per second.

* There is no support for schema updates. After you create a connection setup, there's no way to update the schema. You can only delete and re-create the connection.

* There is a connection limit. Each tenant can create up to 10 connections.

* Edit support for connection is not available. Once the connection has been created, you can't edit or change it. If you need to change any details, you must delete and recreate the connection.
