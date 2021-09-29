---
title: "Manage result types"
ms.author: jeffkizn
author: jypal
manager: jeffkizn
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
ROBOTS: NOINDEX
description: "Manage result types on the search results page"
---

# Manage result types

You can define how search results are displayed one the search results page by designing the layout using result types. The result layout lets you show useful information directly in the search results so users can easily see if they found what they're looking for.

Built-in content types like files and people have a standard layout that can't be modified. Result types are used for [Graph Connectors](connectors-overview.md) content. When you configure a connector and map labels and content properties to source properties, Microsoft Search will use a default search result layout for the content. The label *title* is the most important; you should always have a property assigned to this label to use the default result layout. However, creating a custom result type for your connector content can make those results more impactful for your users.

## Understanding result types

Create your own search result layout and override the default search result layout by creating a result type. A search result type is a rule that causes distinct kinds of search results to be displayed differently. It consists of the following parameters:

- **One or more conditions** to compare each search result against. Examples of conditions are content source and title.
- A **result layout** to use for search results that meet the conditions. The resulting layout controls how the results that meet the conditions appear on the search results page.

When using verticals and connector content, you must create at least one result type for results to display on the vertical, if you don't do the appropriate mapping use the default search result layout.

You can use multiple result types for content displayed in a vertical. This may be important when you combine multiple content sources into a single vertical. It can also be used for a more impactful layout even when there is only one content type. For example, in a vertical that displays incident details, you can customize "severity 1" incidents to have more prominent colors and a larger font than "severity 3" incidents.

## Create or update result types

The result type management experience is wizard driven, you're guided through steps to define the name, content source, rules and layout. Result types can be customized at both the organization-level and SharePoint site level.

### Manage organization-level result types

1. In [Microsoft 365 admin center](https://admin.microsoft.com/), go to the [**Result types**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/resulttypes) page in the **Customization** section.
1. To create a new result type, click **Add** or select an existing one to edit it.
1. Enter a result type name that will help you identify this result type to other search admins. Users won’t see this information.
1. Select a **content source**.
1. Set rules for the result type. If you don’t set rules, the content source is used for the best match.
1. Select **Launch Layout Designer**. You can use an existing layout or create a custom layout and map available properties to layout elements. Copy the JSON script when you're done.
1. After configuring your result type, you can review and save it.

### Manage site-level result types

1. In the Sharepoint site where you want to manage result types, open the settings panel by clicking the gear.
1. Select **Site information**, and then select **View all site settings**.  
1. Look for the Microsoft Search section, and then select **Configure search settings**.
1. In the navigation pane, go to Custom experience, and select the **Result type**.
1. To add a result type, click **Add**. Or, to edit a result type, select the result type in the list.
1. After modifying a result type, you can review and save the result type.
