---
title: "Verticals Overview"
ms.author: jeffkizn
author: jeffkizn
manager: parulm
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Understanding search verticals"
---
# Overview of Verticals

You can use search verticals to customize the results that users see when they search in Microsoft [SharePoint](https://sharepoint.com/), [Microsoft Office](https://office.com), and Microsoft Search in [Bing](https://bing.com). Verticals make it easier for users to find the information that they have permission to see. For example, you could create a search vertical for marketing analysis data from third-party software for your users in the marketing department. You can also define result types and customize the layout for this data.  

You can create verticals and result types at these levels:

- **Organization level** – When you add a vertical at the organization level, it appears on the search results page when users search from their [SharePoint](https://sharepoint.com/) start page, on [Office](https://office.com), or on [Bing](https://bing.com).
- **Site level** – For example, you might want to enable your customer service employees to search for *Severity 1* incidents directly from their department’s SharePoint site.

## Search verticals explained

At the top of the Microsoft Search results page, there's a row of tabs. These are the search verticals. A search vertical only shows results of a certain type or from certain content. Examples are **Files** or **News**. By default, Microsoft Search shows the verticals **All**, **People**, **Files**, **Sites**, and **News**.  

You can add search verticals that are relevant to your organization. These will appear on the Microsoft Search results page in [SharePoint](https://sharepoint.com/), [Office](https://Office.com), and [Bing](https://bing.com). For example, you could create a vertical for marketing-related content and another for sales, based on the type of information that each group needs. You can add verticals to show results only from content indexed via connectors.  

### Multiple connections in a vertical

A search vertical can now surface results from multiple connector sources. This provides greater flexibility in designing your search result page. The existing administrative experience of vertical setup allows you to select multiple connections in the "Content Source" step.
If you accurately appoint as many semantic labels as possible, this experience will be enhanced. You can add semantic labels upon schema definition and ingestion.

[Here](configure-connector.md#step-5-assign-property-labels) is additional information on how to create and manage semantic labels.

> [!NOTE]
> Multiple connections in a vertical is currently in preview. For more information about preview, see [Connectors preview features](connectors-overview.md#what-are-the-preview-features).

### Things you should know

1. A connection can be added as a content source only under one vertical. Reusing connections under multiple verticals is not allowed.
2. If you need to setup a query for a search vertical where multiple connection sources have been added, common source properties should be used to create a such a query.

### Next Steps

[Manage verticals](customize-search-page.md)
[Manage the results layout](customize-results-layout.md)
