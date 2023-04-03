--- 

title: "Result Layout for Confluence cloud Graph connector" 
ms.author: vivg 
author: vivg 
manager: harshkum 
audience: Admin
ms.audience: Admin 
ms.topic: article 
ms.service: mssearch 
ms.localizationpriority: medium 
search.appverid: 
- BFB160 
- MET150 
- MOE150 
description: "Result layout JSON for Confluence cloud connector for Microsoft Search" 
ms.date: 03/08/2023
---

# Result layout for Confluence cloud Graph connector

The [Confluence cloud Graph connector](confluence-cloud-connector.md) allows your organization to index Confluence content. After you configure the connector and index data from the Confluence site, end users can search for those contents in Microsoft Search.

To set up the search result page, you need to:
1. Set up [search vertical](manage-verticals.md).
2. Set up [search result type](manage-result-types.md).

In this document, we have provided a sample result layout JSON required for setting up your result layout for Confluence cloud connector.

## Before you get started

You must have configured the Confluence cloud Graph connector. To consume the sample result layout JSON as is, you must select the below properties for indexing with mentioned [search schema](configure-connector.md).

> [!NOTE]
> * **Retrieve** search attribute is required for displaying a property in search result template. A property can have other search attributes also.  

| Property | Search schema attribute required |
| -------- | -------- |
| Title | Retrieve |
| URL | Retrieve |
| UpdatedByName | Retrieve |
| UpdatedOn | Retrieve |
| Content | Content property |

## Result layout

With this sample, your search results will look like:

![Example of a layout for Confluence cloud connector.](media/confluence-cloud-connector-example-layout.png)

And here's the layout's associated JSON file:


```json
{
    "type": "AdaptiveCard",
    "version": "1.3",
    "body": [
        {
            "type": "ColumnSet",
            "columns": [
                {
                    "type": "Column",
                    "width": "auto",
                    "items": [
                        {
                            "type": "Image",
                            "url": "https://searchuxcdn.blob.core.windows.net/designerapp/images/DefaultMRTIcon.png",
                            "horizontalAlignment": "center",
                            "size": "small"
                        }
                    ],
                    "horizontalAlignment": "center"
                },
                {
                    "type": "Column",
                    "width": "stretch",
                    "items": [
                        {
                            "type": "ColumnSet",
                            "columns": [
                                {
                                    "type": "Column",
                                    "width": "auto",
                                    "items": [
                                        {
                                            "type": "TextBlock",
                                            "text": "[${Title}](${Url})",
                                            "weight": "bolder",
                                            "size": "medium",
                                            "maxLines": 3,
                                            "color": "accent"
                                        }
                                    ],
                                    "spacing": "none"
                                }
                            ],
                            "spacing": "small"
                        },
                        {
                            "type": "TextBlock",
                            "text": "[${Url}](${Url})",
                            "spacing": "small",
                            "weight": "bolder",
                            "color": "dark"
                        },
                        {
                            "type": "Container",
                            "items": [
                                {
                                    "type": "TextBlock",
                                    "text": "**${UpdatedByName}** modified {{DATE(${UpdatedOn})}}",
                                    "spacing": "small",
                                    "$when": "${UpdatedByName!='' && UpdatedOn!=''}"
                                },
                                {
                                    "type": "TextBlock",
                                    "text": "Modified on {{DATE(${UpdatedOn})}}",
                                    "spacing": "small",
                                    "$when": "${UpdatedByName=='' && UpdatedOn!=''}"
                                },
                                {
                                    "type": "TextBlock",
                                    "text": "Modified by __${UpdatedByName}__",
                                    "spacing": "small",
                                    "$when": "${UpdatedByName!='' && UpdatedOn==''}"
                                }
                            ],
                            "spacing": "small"
                        },
                        {
                            "type": "TextBlock",
                            "text": "${ResultSnippet}",
                            "maxLines": 2,
                            "wrap": true,
                            "spacing": "small"
                        }
                    ],
                    "spacing": "medium"
                }
            ]
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "$data": {
        "UpdatedOn": "2019-09-25T06:08:39Z,SHORT",
        "ResultSnippet": "Marketing team at Contoso.., and looking at the Contoso Marketing documents on the team site. This contains the data from FY20 and will taken over to FY21...Marketing Planning is ongoing for FY20..",
        "UpdatedByName": "Amanda Brady",
        "Url": "https://modernacdesigner.azurewebsites.net",
        "Title": "Contoso Marketing Analysis - Q3 FY18"
    }
}

```
## Resources

[Customize search result page](customize-search-page.md)

[Manage search result layouts](customize-results-layout.md)
