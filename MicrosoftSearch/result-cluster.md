---
title: "Connectors result cluster"
ms.author: masingh
author: maheshsinghania
manager: jeffkizn
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
ms.date: 04/07/2022
search.appverid:
- BFB160
- MET150
- MOE150
description: "Details of the Connectors Result Cluster experience"
---
# Manage result clusters

With Graph connectors result clusters, you can search for content from third-party data sources in the All tab, in SharePoint, Office.com, and Microsoft Search in Bing. 

Results in a cluster are grouped together based on the search vertical configuration. Also, each cluster only contains results from a single custom search vertical. To ensure discovery of content in result cluster, the system expects meaningful titles on your items.

Result clusters are displayed on the All vertical and can include maximum two results from a custom vertical. The result cluster experience is turned on by default. 
These SharePoint results for the query bing wiki include a result cluster from the ContosoWiki vertical with two relevant results, BingWiki Main page and OSG Wiki. 

![Example of a MediaWiki result cluster.](media/result-cluster/result-cluster-example.png)

## Check list for result clusters
### Step 1: Check connection schema property settings
Please ensure that your connected content meets the following two criteria, because only then can it show up in a result cluster:

1.	The external connection and its items must have the (body) [“content” property](/graph/api/resources/externalconnectors-externalitem?view=graph-rest-beta#properties) populated with textual content. The content property should be a meaningful and plain-text representation of the item.
2.	One of the source properties must be mapped to the [semantic label “title”](configure-connector.md?#step-6-assign-property-labels).

### Step 2: Check result type definition to adjust the user experience

You control how the results appear in the cluster by defining a [result type](/manage-result-types). If no result type is configured, a  [system generated layout](/customize-search-page#default-search-result-layout) is used.

### Step 3: Verify a result cluster appears on the All results page

Each cluster also includes a heading with the name of the custom vertical and a link to the custom vertical (‘more _CustomVerticalName_ results’). Please note that you can see updates related to result clusters e.g. schema updates or experience modifications via result cluster, only after some time (~10 minutes). 

### How connector results are selected and displayed
When you search, the system identifies which of the custom verticals has the most relevant content results for the query. To do this, for each item in the custom vertical, it looks at the title and displayed content properties and how much the query overlaps with them. Based on the overlap, the two top ranking results from that vertical appear in a result cluster on the All page.

In this example, you can see the query term bing wiki occurs in both titles and the displayed body content of the results. Because of this overlap, they are included in a result cluster on the All results page.

![Highlighted overlapping terms in title and display properties of result clusters](https://user-images.githubusercontent.com/72018014/183807100-64aa10c7-449a-4fcb-bbff-e2c35170ebcc.png)

> [!NOTE]
> For single term-queries the likelihood is low that a result cluster is shown with an item whose title or body content does not contain the single query term. Of course, for longer queries where only one query term matches the item’s title or body content, the likelihood that a result cluster is shown is higher. 
>
> In some cases an overlap in just the title or only the content triggers a result cluster because there are no higher relevant results on other verticals.
> 
> Even if there was an overlap in both title and content, a result cluster might not be shown for a specific custom vertical because other custom verticals have results with higher overlap in title and content properties.

### Recommendations
To ensure discovery of content from the search verticals, we recommend attributing the semantic label “title” to a property that describes the item and functions as the “title” of an item. The "content" property should also represent the item, for example, it could be the description of the items of a connection. Choosing both the title and content priorities will provide the best experience for your users through accurate triggering of the result cluster and most relevant results in the cluster.

> [!TIP]
> Please ensure to provide meaningful titles for your items, which summarizes well an item. This increases the likelihood of the desired content showing up in a result cluster. For example, avoid the use of IDs as values for the property "title" unless your users are using IDs to look for content.
> 
> If your content does not have meaningful titles, you can create a Custom field that describes better what the content is about and can function as “title”. 
>
> Please also ensure that the body “content” of your items is a meaningful, representative summary or description of the item. Concatenating incoherent or disjoint pieces of text can have a detrimental effect on the result cluster triggering.
