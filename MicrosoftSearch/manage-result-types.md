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

You can define how search results are displayed on the search results page by [designing the layout](customize-results-layout.md) using result types. The result layout lets you show useful information directly in the search results so users can quickly find the information they need.

Built-in content types like files and people have a standard layout that can't be modified. Result types are used for [Graph Connectors](connectors-overview.md) content. When you configure a connector with property mappings, Microsoft Search will use a default search result layout for the connector search results. The label *title* is the most important; you should always have a property assigned to this label to use the default result layout. However, creating a custom result type for your connector content can make those results more impactful for your users.

When using verticals and connector content, you must create a result type or do the mappings for a default layout. If you do not do either, the vertical will not display any search results.

## Understanding result types

Create your own [search result layout](customize-results-layout.md) and override the default search result layout by creating a result type. A search result type is a rule that causes distinct kinds of search results to be displayed differently. It consists of the following parameters:

- **One or more conditions** to compare each search result against. Examples of conditions are content source and title.
- A **result layout** to use for search results that meet the conditions. The resulting layout controls how the results that meet the conditions appear on the search results page.

You can use multiple result types for content displayed in a vertical. This may be important when you combine multiple content sources into a single vertical. It can also be used for a more impactful layout even when there is only one content type. For example, in a vertical that displays incident details, you can customize "high severity" incidents to have more prominent colors than "low severity" incidents. This can be done by defining conditions on the 'severity' property in the **Rules** section.

## Create or update result types

The result type management experience is wizard driven, you're guided through steps to define the name, content source, rules, and layout. Result types can be customized at both the organization-level and SharePoint site level.

### Manage organization-level result types

1. In [Microsoft 365 admin center](https://admin.microsoft.com/), go to the [**Result types**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/resulttypes) page in the **Customization** section.
2. To create a new result type, click **Add** or select an existing one to edit it.
3. After configuring your result type, you can review and save it.

### Manage site-level result types

1. In the SharePoint site where you want to manage result types, open the settings panel by clicking the gear.
2. Select **Site information**, and then select **View all site settings**.  
3. Look for the Microsoft Search section, and then select **Configure search settings**.
4. In the navigation pane, go to Custom experience, and select the **Result type**.
5. To add a result type, click **Add**. Or, to edit a result type, select the result type in the list.
6. After modifying a result type, you can review and save the result type.

## Troubleshooting

Here's a list of common problems you might see and actions to fix them.

|Problem  |Action  |
|---------|---------|
| I don't see my result layout on the search page, although I created one. | There may be a delay of a few minutes because these settings are cached. Wait a few minutes and try again.        |
| I don't see any content sources on the result type page. | Make sure you have configured connectors and indexed data.   |
| StringCollection properties do not bind to the result type and render as “${propertyName}”  | Ensure properties of type StringCollection are wrapped in a join method as:  **${join(propertyName, ‘,’)}**. If you want to show a single value (say, the ith item) from a StringCollection, you can specify it as follows: **${propertyName[i]}**  (Note: indexing in StringCollection types start from 0)    |
