---
title: Overview and concepts for Microsoft Graph Connectors
description: Add a short description
services: skype-for-business-online-admin
author: monaray
manager: samanro
layout: LandingPage
ms.assetid: 
ms.service: mssearch
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: landing-page
ms.date: 10/10/2019
ms.author: monaray
---

# Overview and concepts for Microsoft Graph Connectors

#### In this article
* <a href="#connectors">What are connectors?</a>
* <a href="#types">Types of connectors</a>
* <a href="#office365">Office 365 plans we support</a>
* <a href="concepts">Connector concepts</a>

<h2 id="connectors">What are connectors?</h2>

Microsoft Search indexes all your Microsoft 365 data to enable search. Connectors allow your organization to ingest and index third-party data for use in Microsoft Search. This third-party data can be hosted on-premises or in the public or private cloud. Connectors allow your organization to expand the breadth of information searchable from your Microsoft Search application to enhance your search capabilities. 


<h2 id="types">Types of connectors</h2>

### Connectors by Microsoft
Microsoft provides ready to configure out-of-the-box connectors available to set up from the M365 admin portal. Below you can check out the connectors Microsoft provides and learn how to [configure your Microsoft built-in connector](configure-connector.md).

<ul class="panelContent cardsZ">
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardText">
                        <h3>Azure Data Lake Storage Gen2</h3>
                        <p>by <a href="https://www.microsoft.com">Microsoft</a></p>
                        <p>The Azure Data Lake Storage Gen2 connector for Microsoft Search will allow your organization to search for files and their content stored in Azure Blob Containers and hierarchy enabled folders within a given Azure Data Lake Storage Account.</p>
                        <p><a href=azure-data-lake-connector.md>More details</a> <img src="Azure_Data_Lake_Small.png" alt="ADLS logo" width="35" height="35" align="right"></p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardText">
                        <h3>Enterprise Website</h3>
                        <p>by <a href="https://www.microsoft.com">Microsoft</a></p>
                        <p>The enterprise website connector for Microsoft Search will allow your organization to search for files and their content stored in any non-Sharepoint enterprise website.</p> <a href=enterprise-web-connector.md>More details</a> <img src="IntranetSites_Small.png" alt="Enterprise Website" width="35" height="35" align="right"></p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardText">
                        <h3>File share</h3>
                        <p>by <a href="https://www.microsoft.com">Microsoft</a></p>
                        <p>The file share connector for Microsoft Search will allow your organization to search for on-premises file shares.</p>
                        <p><a href=file-share-connector.md>More details</a> <img src="FileConnectorLogo_Small.png" alt="ADLS logo" width="35" height="35" align="right"></p>
                    </div>
                </div>
            </div>
        </div>
    </li>
</ul>
<ul class="panelContent cardsZ">
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardText">
                        <h3>MediaWiki</h3>
                        <p>by <a href="https://www.microsoft.com">Microsoft</a></p>
                        <p>The MediaWiki connector for Microsoft Search will allow your organization to search for MediaWiki articles through your registered account.</p>
                        <p><a href=mediawiki-connector.md>More details</a> <img src="MediaWiki_Small.png" alt="Enterprise Website" width="35" height="35" align="right"></p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardText">
                        <h3>Microsoft SQL</h3>
                        <p>by <a href="https://www.microsoft.com">Microsoft</a></p>
                        <p>The Microsoft SQL connector for Microsoft Search will allow your organization to search data housed in on-premises SQL databases.</p>
                        <p><a href=MSSQL-connector.md>More details</a> <img src="SqlConnectorLogo_Small.png" alt="Enterprise Website" width="35" height="35" align="right"></p>
                    </div>
                </div>
            </div>
        </div>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardText">
                        <h3>ServiceNow</h3>
                        <p>by <a href="https://www.microsoft.com">Microsoft</a></p>
                        <p>The ServiceNow connector for Microsoft Search will allow your organization to search for knowledge-based articles from your application.</p>
                        <p><a href=servicenow-connector.md>More details</a> <img src="ServiceNow_Small.png" alt="Enterprise Website" width="35" height="35" align="right"></p>
                    </div>
                </div>
            </div>
        </div>
    </li>
</ul>
 

### Connectors by our partners
Check out our [connector catalog](connectors-catalog.md) to learn what connectors our partners support and contact them to utilize their connector solutions. You can manage your connectors from our partners in the M365 admin portal as well. 

### Build your own connector
Developers can use Microsoft Graph to create connectors to index custom types or files. A connector is an application that uses the Microsoft Graph indexing API to create a connection and push items into the search index. For more information, see the Microsoft Search indexing API overview.
( NEED TO INSERT LINKS ABOVE ^^^^ )


<h2 id="office365">Office 365 plans we support</h2>

Microsoft Graph Connectors are only supported by the following Office 365 plans:
* [Enterprise](https://www.microsoft.com/en-us/microsoft-365/compare-all-microsoft-365-plans) E3 & E5
* [Education](https://www.microsoft.com/en-us/microsoft-365/academic/compare-office-365-education-plans?activetab=tab:primaryr1) A3 & A5

To learn more about these plans, refer to Office 365 products [website](https://products.office.com/en-us/compare-all-microsoft-office-products-b?&t41437&activetab=tab:primaryr1). 

Once you have your admin login credentials, you can log into the Microsoft 365 admin portal and [manage your connector](manage-connector.md).


<h2 id="concepts">Connector concepts</h2>

#### High-level architecture
{ INSERT GRAPHIC HERE = what does the graphic look like for MS-built connectors vs partner vs build your own? } 

#### Data source
The data source is the third-party data you want to be indexed and stored in the Microsoft Search index. The data source can either live on-premises or in the cloud.

#### Connection 
A connection to a data source entails proper access to the data (authentication), traversal of the document repository, and feeding of the data to the graph connector service for indexing. 

#### Search schema 
The search schema is a set of search attributes associated with the set of managed properties—these attributes enable search functionalities of the different properties and help determine what results are displayed on the search results page and what results are searchable from the end user experience. The following attributes are supported and enable the following functionalities:

**Managed Property Setting** | **What it does** | **Example**
--- | --- | ---
*Searchable* | Enables the text content of the property to be searched for. The content of this property is included in the full-text index. | If the property is “Title,” a query for “Enterprise” returns items that contain the word “Enterprise” and items with “Enterprise” in the title
*Queryable* | Enables searching for a match for that particular property. The property name must be specified in the query either programmatically or verbatim. | If the property is “Title,” a query must contain “Title: Enterprise.”
*Retrievable* | Enables the content of this property to be displayed in the search results. | 

#### Custom search application 
A software application built on top of Microsoft Graph APIs that enables custom search capabilities and custom search interfaces. Customizable search capabilities include search rankings, filtering results, and data source reporting. Learn how to build your own application experience on top of M365 and third-party data here. 
( INSERT LINKS ABOVE ) ^^^

#### Search user interface
The user interface (UI) used by your employees or customers to search content from your Microsoft Search application. Learn how to customize your search UI by creating your verticals and modern result types here.
( INSERT LINKS ABOVE ) ^^^

