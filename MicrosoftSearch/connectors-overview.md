---
title: "Connectors Overview"
ms.author: monaray
author: monaray97
manager: shohara
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

# Overview of Microsoft Graph connectors

[Microsoft Search](https://docs.microsoft.com/microsoftsearch/overview-microsoft-search) indexes all your [Microsoft 365](https://www.microsoft.com/microsoft-365) data to make it searchable for users. With Microsoft Graph connectors, your organization can index third-party data so it appears in Microsoft Search results. This expands the types of content sources that are searchable in your Microsoft 365 productivity apps and the broader Microsoft ecosystem. The third-party data can be hosted on-premises or in the public or private clouds.

<!---link Microsoft Graph reference in line 19 when we have access to relevant documentation--->

The rest of this article is intended to help Microsoft 365 administrators locate the resources that are avaiable to answer the following questions:

* [What data sources can be connected to Microsoft Search?](#what-data-sources-can-be-connected-to-microsoft-search)
* [How do I manage my connections?](#how-do-i-manage-my-connections)
* [What are the license requirements and terms of use for Graph connectors?](#what-are-the-license-requirements-and-terms-of-use-for-graph-connectors)
* [How do I customize and configure search results?](#how-do-i-customize-and-configure-search-results)
* [How do I search my connector data from a custom application?](#how-do-i-search-my-connector-data-from-a-custom-application)

<!---Modify to another note that is more accurate--->
> [!IMPORTANT]
> Microsoft Graph connectors and Microsoft Search APIs are now globally available. The first rollouts will be to customers configured for  targeted release. If you want to use a Graph connector in your tenant, be sure to opt into [Targeted release](https://docs.microsoft.com/office365/admin/manage/release-options-in-office-365?view=o365-worldwide).

<!---Add Value, scenario, example, and/or graphic in December updates--->
<!---Probably remove architecture section below
## Architecture

The following architectural diagram of the Microsoft Graph platform shows how Graph connector content flows through content indexing to user results in [Microsoft Search](https://docs.microsoft.com/microsoftsearch/overview-microsoft-search) clients. The rest of this section explains each of the key building blocks in the diagram.


![Diagram: on-premises and cloud-based data is pulled by connectors and indexed by the Microsoft Search API, and then the Microsoft Search service delivers the results to users.](media/highlevel-connectors_FINAL.png)


Graph connectors can pull data from cloud-based (SaaS) data sources and on-premises data stores. The above diagram shows connections to only two data sources, but you can add connections to up ten sources per tenant.

The Microsoft Graph Connectors API instantiates one connection per data source. Then, the API indexes and stores the data. Established connections interact with Microsoft Search, so users can get search results.

You can use the Microsoft 365 Microsoft 365 [admin center](https://admin.microsoft.com) to setup and manage any of the Graph connectors by Microsoft. The admin center has a simple user interface that makes it easy to establish the connection to your data source, and monitor connection status and utilization.

***Edit paragraph below***
To create a **connection** to a data source, admins need authenticated access to the data and the entire content repository. The data is fed to the graph connector service for indexing.--->

## What data sources can be connected to Microsoft Search?

Microsoft created ten out-of-the box Graph connectors, and our ecosystem partners have created over 100 additional Graph connectors. You can also build your own Graph connector. 

### Graph connectors by Microsoft

You can connect to the following data sources using Graph connectors created by Microsoft:

<!---Need to add a few links below when docs exist--->
* [Azure Data Lake Storage Gen2](azure-data-lake-connector.md)
* [Azure DevOps](azure-devops-connector.md)
* Azure SQL
* [Enterprise websites](enterprise-web-connector.md)
* [MediaWiki](mediawiki-connector.md)
* [Microsoft SQL Server](MSSQL-connector.md)
* On-prem file share
* Oracle (preview)
* Salesforce (preview)
* [ServiceNow](servicenow-connector.md)

The [Graph connectors gallery](connectors-gallery.md) contains a brief description of each of these Graph connectors. If you are ready to connect one of these data sources to your tenant, be sure to read the [General setup instructions](configure-connector.md) and any other articles in the Setup connectors by Microsoft section that apply to your data source.

### Graph connectors by our partners

The [Microsoft Graph connectors gallery](connectors-gallery.md) includes a brief descriptions of each of the Graph connectors created by our partners and a link to each partner's website. Contact each partner directly to learn more.

### Build your own Graph connector

If you plan to build your own Graph connector, see the [Overview of the Microsoft Search API in Microsoft Graph](https://docs.microsoft.com/graph/search-concept-overview)
 for more information.

## How do I manage my connections?

You can manage your connections from the [Connectors tab](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/Connectors) in the [Microsoft 365 admin center](https://admin.microsoft.com/). See [Manage your connections](manage-connector.md) for more information.

## What are the license requirements and terms of use for Graph connectors?

You need a valid Microsoft 365 or Office 365 license and sufficient Graph Connectors quota for users in your organization to view data from connectors in their search results.

To learn more, see [License requirements and pricing](licensing.md) and [Terms of use](terms-of-use.md).

## How do I customize and configure search results?

There are a number of ways to customize and configure search results. See the following articles to learn more:
<!---Need links for first two articles below--->
* Manage search verticals and result types
* Manage search result layouts
* [Result cluster experience](result-cluster.md)
* [Custom filters](custom-filters.md)

## How do I search my connector data from a custom application?

After custom data is indexed, developers can [query this data](https://docs.microsoft.com/graph/search-concept-custom-types). You can view your data in any application. For more information, see the [Overview of the Microsoft Search API in Microsoft Graph](https://docs.microsoft.com/graph/search-concept-overview).
