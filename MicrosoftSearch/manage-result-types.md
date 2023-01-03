---
title: "Manage result types"
ms.author: jypal
author: jypal6
manager: jeffkizn
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
description: "Manage result types on the search results page"
---

# Manage result types

Microsoft search provides a default search result layout experience for the different types of content shown in the search results page. For some content, you can override this default search layout and change the search result experience by [designing the layout](customize-results-layout.md) using result types. This can be done to display richer layout with useful information in the search results so users can quickly find the information they need.

Result types can be used for select SharePoint content and [Graph Connectors](connectors-overview.md) content . Search results for SharePoint list items, SharePoint sites, SharePoint pages and Portable document format(PDFs) can be changed using result types. Content types like files(non-PDF) and people have a standard layout that can't be modified.

For Graph connector search results, when you configure a connector with property mappings, Microsoft Search will use a default search result layout for the connector search results. The label *title* is the most important; you should always have a property assigned to this label to use the default result layout. However, creating a custom result type for your connector content can make those results more impactful for your users. When using verticals and connector content, you must create a result type or do the mappings for a default layout. If you do not do either, the vertical will not display any search results.


## Understanding result types

A result type is a configuration that causes search result layout to be changed as per the design in configuration. It consists of the following parameters:

- **One or more conditions** to compare and match each search result with the configuration. Examples of conditions are content source and rules.
- A **result layout** to use for search results that meet the conditions. The resulting layout controls how the results that meet the conditions appear on the search results page.

You can use multiple result types for content displayed in a vertical. This may be important when you combine multiple content sources into a single vertical. It can also be used for a more impactful layout even when there is only one content type. For example, in a vertical that displays incident details, you can customize "high severity" incidents to have more prominent colors than "low severity" incidents. This can be done by defining conditions on the 'severity' property in the **Rules** section.

Each result type has a priority which determines the order of match evaluation. This is significant if multiple matching result types are found for a given search result. In such cases, the result type with higher priority is applied to the search result. Hence, it is important to ensure that a generic result type has lower priority and result types with multiple conditions have higher priority.

## Create or update result types

The result type management experience is wizard driven, you're guided through steps to define the name, content source, rules, and layout. Result types can be customized at both the organization-level and SharePoint site level.

> [!NOTE]
> Result types for "SharePoint and OneDrive" content source is available in Targeted release ring at Organization level for SharePoint and Office.com canvases only. 

### Manage organization-level result types

1. In [Microsoft 365 admin center](https://admin.microsoft.com/), go to the [**Result types**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/resulttypes) page in the **Customization** section.
2. To create a new result type, click **Add** or select an existing one to edit it.
3. After configuring your result type, you can review and save it.

### Manage site-level result types

1. In the Sharepoint site where you want to manage result types, open the settings panel by clicking the gear.
2. Select **Site information**, and then select **View all site settings**.  
3. Look for the Microsoft Search section, and then select **Configure search settings**.
4. In the navigation pane, go to Custom experience, and select the **Result type**.
5. To add a result type, click **Add**. Or, to edit a result type, select the result type in the list.
6. After modifying a result type, you can review and save the result type.


## Limitations

1. Custom SharePoint managed properties cannot be used in the ‘Rules’ section of result type  
2. Result types created for "SharePoint and OneDrive" content source does not apply to search results on Microsoft Search in Bing canvases. 
3. If the search scope in a SharePoint site has been changed to hub or Organization scope, the result type created at site level will be applied to search results instead of honoring the result types at hub or Organization scope. In such cases, do not create site level result types to ensure search experience consistency with the change in scope. 

## Troubleshooting

Here's a list of common problems you might see and actions to fix them.

|Problem  |Action  |
|---------|---------|
| I don't see my result layout on the search page, although I created one. | There may be a delay of a few minutes because these settings are cached. Wait a few minutes and try again.        |
| I don't see any content sources on the result type page. | Make sure you have configured connectors and indexed data .   |
