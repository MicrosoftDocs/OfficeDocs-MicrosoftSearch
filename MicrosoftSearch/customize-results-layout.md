---
title: "Customize the search results layout"
ms.author: anfowler
author: adefowler
manager: shohara
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Using adaptive cards, create a layout to view your customized search results"
---
# Create a layout to customize search results

You use the [Adaptive Cards Template language](https://docs.microsoft.com/adaptive-cards/templating/language) to create a result layout and its associated JSON file to define a result type by using the layout designer. 

You can create the result layout using the search layout designer in following ways: 

- Use pre-defined search results layouts from the layout designer as-is if you find a design that meets your needs. 
- Start with a pre-defined layout, and then edit it to meet your needs. 
- Start with a blank layout and create your own.

## Things to consider...

Before you get started, there are a few things that you should do and a few things you should avoid to ensure that your layouts will be successful.

### Do

- Provide logos in the result properties or in the layout JSON.  
- Verify the result layout if any of the result property values are not present. Use `$when` condition to hide an element if the property doesn't exist.  
- Make sure that data types of the `$when` condition and the result property match. For example, don't compare `Number` with `Text` in `$when` condition.  
- Images and logos must be chosen so that they work with light and dark theme. 
- Use the `wrap` and `maxLines` properties so that the `Textblock` element can handle dynamic content.  
- Properly format the date when using `{DATE()}` in markdown.  

### Don't

- Don't define invalid data types when binding values. For more information about the data types, see [Manage the Search schema](https://docs.microsoft.com/sharepoint/search/manage-the-search-schema ).
- Avoid cropping the result on the result page by following the maximum height of the result layout JSON. If you exceed the maximum height of the result layout the result will be cropped on the result page.
- Don't use `px` values in properties of element.

## Create a layout on your own
Creating a layout on your own requires knowledge of adaptive cards and their schema. Search result layout uses a subset of the elements offered by adaptive cards and you can use the layout designer to learn about the supported set of elements.  

While creating your own layout, create the adaptive card layout using sample data, and then finalize the layout.

In this example, we're showing a layout with a header, link, and descriptive text.

![Example of a layout with a header, link, and description.](media/Verts-ExampleLayout.png)

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

                    "width": 8, 

                    "items": [ 

                        { 

                            "type": "TextBlock", 

                            "text": "Contoso Marketing Analysis - Q3 FY18", 

                            "color": "Accent", 

                            "size": "Medium", 

                            "spacing": "None", 

                            "$when": "{title != \"\"}", 

                            "weight": "Bolder" 

                        }, 

                        { 

                            "type": "TextBlock", 

                            "text": "https://contoso.com/hr/link", 

                            "spacing": "None", 

                            "color": "Dark", 

                            "weight": "Bolder" 

                        }, 

                        { 

                            "type": "TextBlock", 

                            "text": "Marketing team at Contoso.., and looking at the Contoso Marketing documents on the team site. This contains the data from FY20 and will taken over to FY21...Marketing Planning is ongoing for FY20..", 

                            "wrap": true, 

                            "maxLines": 2, 

                            "spacing": "Medium" 

                        } 

                    ], 

                    "horizontalAlignment": "Center", 

                    "spacing": "None" 

                } 

            ] 

        } 

    ], 

    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json" 

}
```

You can then use the You can then use the [Adaptive Cards Template](https://docs.microsoft.com/adaptive-cards/templating)

You can then use adaptive card templating to abstract the layout from the data by binding the layout fields to the variables.

Here's Layout JSON after binding the data:


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

                    "width": 8, 

                    "items": [ 

                        { 

                            "type": "TextBlock", 

                            "text": "[{title}]({titleUrl})", 

                            "color": "Accent", 

                            "size": "Medium", 

                            "spacing": "None", 

                            "weight": "Bolder" 

                        }, 

                        { 

                            "type": "TextBlock", 

                            "text": "{link}", 

                            "spacing": "None", 

                            "color": "Dark", 

                            "weight": "Bolder" 

                        }, 

                        { 

                            "type": "TextBlock", 

                            "text": "{description}", 

                            "wrap": true, 

                            "maxLines": 2, 

                            "spacing": "Medium" 

                        } 

                    ], 

                    "horizontalAlignment": "Center", 

                    "spacing": "None" 

                } 

            ] 

        } 

    ], 

    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json" 

}
```

Sample data: 
{ 

    "title": "Contoso Marketing Analysis - Q3 FY18", 

    "titleUrl": "https://contoso.com/hr/link", 

    "link": "https://contoso.com/hr/link", 

    "description": "Marketing team, and looking at the Contoso Marketing documents on the team site. Yo can't see right...Marketing Planning presentation?" 

} 

## Map the layout to the result properties

You must map each field of the layout to a result property or a connector property to generate the result layout JSON.

![Verts-SearchLayoutDesigner.png](media/Verts-SearchLayoutDesigner.png)

Select a field in the layout to highlight the variables that need to be mapped. You can use multiple variables for a single field and all fields must be mapped to the result properties.
