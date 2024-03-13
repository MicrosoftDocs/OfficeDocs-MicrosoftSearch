--- 

title: "Result Layout for Azure DevOps Wiki Graph connector" 
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
description: "Result layout JSON for Azure DevOps Wiki connector for Microsoft Search" 
ms.date: 06/03/2022
---

# Result layout for Azure DevOps Wiki Graph connector

The [Azure DevOps Wiki Graph connector](azure-devops-wiki-connector.md) allows your organization to index wikis from Azure DevOps service. After you configure the connector and index content, you need to set up a search result page.

To set up the search result page, you need to:
1. Set up [search vertical](manage-verticals.md).
2. Set up [search result type](manage-result-types.md).

In this document, we have provided a sample result layout JSON required for setting up your result layout for Azure DevOps Wiki connector.

## Before you get started

You must have configured the Azure DevOps Wiki Graph connector. To consume the sample result layout JSON as is, you must select the below properties for indexing with mentioned [search schema](configure-connector.md).

> [!NOTE]
> * **Retrieve** search attribute is required for displaying a property in search result template. A property can have other search attributes also.  

| Property | Search schema attribute required |
| -------- | -------- |
| Title | Retrieve |
| RemoteURL | Retrieve |
| LastPublishedAuthorName | Retrieve |
| LastPublishedDate | Retrieve |
| Content | Content property |
| Organization | Retrieve |
| Project | Retrieve |
| WikiIdentifier | Retrieve |

## Result layout

With this sample, your search results will look like:

![Example of a layout for Azure DevOps Wiki connector.](media/azure-devops-wiki-connector-example-layout.png)

And here's the layout's associated JSON file:


```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
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
                            "url": "https://searchuxcdn.blob.core.windows.net/designerapp/images/AzureDevOpsLogo.png",
                            "horizontalAlignment": "Center",
                            "altText": "Not available",
                            "width": "-1px",
                            "size": "Small"
                        }
                    ]
                },
                {
                    "type": "Column",
                    "width": 8,
                    "items": [
                        {
                            "type": "TextBlock",
                            "text": "[${Title}](${RemoteURL})",
                            "color": "Accent",
                            "size": "Medium",
                            "weight": "Bolder"
                        },
                        {
                            "type": "TextBlock",
                            "text": "__${LastPublishedAuthorName}__ modified on {{DATE(${LastPublishedDate})}}",
                            "spacing": "Small"
                        },
                        {
                            "type": "ColumnSet",
                            "columns": [
                                {
                                    "type": "Column",
                                    "width": "stretch",
                                    "items": [
                                        {
                                            "type": "TextBlock",
                                            "text": "__Organization:__ ${Organization}"
                                        }
                                    ]
                                },
                                {
                                    "type": "Column",
                                    "width": "stretch",
                                    "items": [
                                        {
                                            "type": "TextBlock",
                                            "text": "__Project:__ ${Project}"
                                        }
                                    ]
                                },
                                {
                                    "type": "Column",
                                    "width": "stretch",
                                    "items": [
                                        {
                                            "type": "TextBlock",
                                            "text": "__Wiki:__ ${WikiIdentifier}"
                                        }
                                    ]
                                }
                            ]
                        },
                        {
                            "type": "TextBlock",
                            "text": "${ResultSnippet}",
                            "wrap": true,
                            "maxLines": 3,
                            "spacing": "Medium"
                        }
                    ],
                    "horizontalAlignment": "Center",
                    "spacing": "Medium"
                }
            ]
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "$data": {
    }
}

```
## Resources

[Customize search result page](customize-search-page.md)

[Manage search result layouts](customize-results-layout.md)
