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
description: "Manage result types on the search results plage"
---

# Customize the search results page
You can create **result types** to customize the search results that users see when they search in Microsoft [SharePoint](https://sharepoint.com/), [Microsoft Office](https://office.com), and Microsoft Search in [Bing](https://bing.com).

## About result Types
You can define how results are displayed in the vertical by designing the layout using result types. The result layout lets you show important information directly in the search results, so users don't have to select each result to see if they found what they're looking for.

### Default search result layout
A default search result layout will be shown for Connector content if *labels and content property have been mapped correctly to the source properties at the time of configuring the connector. The label *title is the most important label. It is *strongly recommended that you have a property assigned to this label to use the default search result layout.

### Create your result type
Create your search result layout and override the default search result layout by creating a result type. A search result type is a rule that causes distinct kinds of search results to be displayed differently. It consists of the following:
- **One or more conditions** to compare each search result against, such as the content source of the search result.
- A **result layout** to use for search results that meet the conditions. The resulting layout controls how the results that meet the conditions appear and behave on a search results page.

You must create at least one result type for results to display on the vertical if you don't do the appropriate mapping to show the default search result layout.

You can create multiple result types for each vertical, which allows you to use different layouts for different types of results. For example, you can customize Severity 1 incidents to have more prominent colors and a larger font than Severity three incidents.

After you start the wizard, you're guided through the steps to define the name, content source, and conditions for the result type. You can define the priority of the result type from the list view.

###  Consider the following factors before creating result types
- Make sure that the connector has been indexed. This can take up to 48 hours, depending on the file size. 
- You can’t create a vertical for content that resides in SharePoint. 

#### Create a result type at the organization level
1. In [Microsoft 365 admin center](https://admin.microsoft.com/), go to **Result types**.   
2. To add a Result type, click **Add**.
3. Enter a result type name that will help you identify this result type to other Search admins.
>[!Note]
>Users won’t see this information.
4. Select a **content source**.
5. Set rules for the result type. If you don’t set rules, the content source is used for the best match.
6. Select **Launch Layout Designer**.
>[!Note]
>You can use an existing layout or create a custom layout and map available properties to layout elements. Copy the JSON script when you're done.
7. After adding a result type, you can review and save the result type.
Or
8. To edit a result type, select the result type from the list.
9. After modifying a result type, you can review and save the result type.

#### Create a result type at the organization level
1. On the [SharePoint](https://sharepoint.com/) site where you want to create the result type, go to **Settings**.
2. Select **Site information** and then click **View all site settings**.
3. Look for the Microsoft Search section, and then select **Configure search settings**.
4. In the navigation pane, go to Custom experience, and select the **Result type** tab.
5. To add a result type, click **Add**. Or, to edit a result type, select the result type in the list.
6. After modifying a result type, you can review and save the result type.
