---
title: "Customize the Microsoft Search page"
ms.author: jeffkizn
author: jypal
manager: jeffkizn
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Add search verticals and customize search results"
---
# Customize the search results page

You can create search verticals and result types to customize the search results that users see when they search in Microsoft [SharePoint](https://sharepoint.com/), [Microsoft Office](https://office.com), and Microsoft Search in [Bing](https://bing.com). Verticals make it easier for users to find the information that they have permission to see. For example, you could create a search vertical for marketing analysis data from third-party software for your users in the marketing department. You can also define result types and customize the layout for this data.  

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
2. If you need to set up a query for a search vertical where multiple connection sources have been added, common source properties should be used to create a such a query.

## Things to consider

Before you start, make sure that the connector has been indexed. This can take up to 48 hours, depending on the file size.

You can’t create a vertical for content that resides in [SharePoint](https://sharepoint.com/).

There are three basic steps to add a vertical:

1. Create the vertical. In this step, you define the vertical’s name, content source, and scope of the content to search.
2. Define what the results for this vertical will look like.  
3. Enable the vertical (to be displayed) from the vertical list page.

## STEP 1: Create the search vertical

After you start the wizard, you're guided through the steps to define the vertical's name, content source, and scope of the content to search. The vertical is created in a disabled state. You'll enable it later.

You can use a limited set of [Keyword Query Language (KQL)](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference) to narrow the scope. This page lists the properties that are available. We recommend that you use free-text keywords and property restrictions with boolean operators for creating the KQL.
KQL also supports the use of [profile query variables](#profile-query-variables) to fine-tune results under the vertical.

### Create a vertical at the organization level

To create the vertical on Microsoft Search in [SharePoint](https://sharepoint.com/) home, [Office](https://office.com), or [Bing](https://bing.com), follow these steps:

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to [**Verticals**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/verticals).
2. Select **Add** to get started.  

### Create a vertical at the site level

1. On the [SharePoint](https://sharepoint.com/) site where you want the vertical, go to **Settings**.
2. Select **Site information** and then **View all site settings**.
3. Look for the **Microsoft Search** section, and then select **Configure Microsoft Search for this site collection**.
4. In the navigation pane, go to **Custom experience**, and then select the **Verticals** tab.
5. To add a vertical, select **Add**.
  Or, to edit a vertical, select it in the list.

Remember, verticals are created in a disabled state. They must be enabled before users can see them.

## STEP 2: Create the result types

You can define how results are displayed in the vertical by designing the layout using result types. The result layout lets you show important information directly in the search results, so users don't have to select each result to see if they found what they're looking for.

### Default search result layout

A default search result layout will be shown for Connector content if **labels** and **content** property have been mapped correctly to the source properties at the time of configuring the connector. The label **title** is the most important label. It is **strongly recommended** that you have a property assigned to this label to use default search result layout.

### Create your own result type

You can decide to create your own search result layout and override the default search result layout by creating a **result type**. A search result type is a rule that causes distinct kinds of search results to be displayed in different ways. It consists of the following:

- **One or more conditions** to compare each search result against, such as the content source of the search result.  
- A **result layout** to use for search results that meet the conditions. The resulting layout controls the way that all results that meet the conditions appear and behave on a search results page.

**If appropriate mapping is not done to show default search result layout, You must create at least one result type for results to display on the vertical.** You can create multiple result types for each vertical, which allows you to use different layouts for different type of results. For example, you can customize *Severity 1* incidents to have more prominent colors and a larger font compared to *Severity 3* incidents.

After you start the wizard, you're guided through the steps to define the name, content source, and conditions for the result type. You can define the priority of the result type from the list view.
  
### Create a result type at the organization level

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to [**Result types**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/resulttypes).
2. To add a **Result type**, select **Add**. To edit a result type, select the result type in the relevant list.

### Create a results type at the site level

1. On the [SharePoint](https://sharepoint.com/) site where you want to create the result type, go to **Settings**.
2. Select **Site information** and then **View all site settings**.
3. Look for the Microsoft Search section, and then select **Configure Microsoft Search for this site collection**.
4. In the navigation pane, go to **Custom experience**, and select **Result type** tab.
5. To add a result type, select **Add**.  Or, to edit a result type, select the result type in the list.

## STEP 3: View the vertical after it's enabled

After you enable the vertical, it will take a few hours before you can view it. If you don't want to wait after enabling it, you can append **cacheClear=true** to the URL in [SharePoint](https://sharepoint.com/) and [Office](https://office.com) to view the vertical immediately. For [Bing](https://bing.com), append **&features=uncachedVerticals** to the Work vertical URL to view the verticals immediately.

> [!NOTE]
> Added verticals will not be visible on [SharePoint](https://sharepoint.com/) and [Office](https://office.com) when viewed from mobile web browsers.

## Profile query variables

Query variables are used in the KQL query section of a vertical to provide dynamic data as an input to the query of a vertical. You can use profile query variables to make the search results contextual to the signed-in user. Profile query variables fetch values from the signed-in user’s [profile](/graph/api/resources/profile?view=graph-rest-beta).

For example, if you want to create a “Tickets” vertical where a signed-in user can search for support tickets assigned to them, you can specify the following query under the "Query" section during the vertical creation in the administration page.  

**AssignedTo:{Profile.accounts.userPrincipalName}**

This will narrow down the search results to show only those items where the assignee is the user performing the search.

[Profile resource](https://docs.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta) exposes properties as collections. For example, information related to email addresses is exposed through email collection, work positions as positions collection, and so on. All properties available in the user profile, which have AAD as the source type, are exposed as Query variables.

Consider a user who has 3 email addresses available in the email collection, as shown below.

```json
"emails": [{ 

        "address": "Megan.Bowen@contoso.com",
        "id": "xyz", 
        "source": { 
            "CreatedBy": "xyz", 
            "CreatedOn": "2222", 
            "Type": "official" 
        },
        "type": "main" 
    }, { 
        "address": "meganb@hotmail.com",
        "id": "abc", 
        "source": { 
            "CreatedBy": "abc",
            "CreatedOn": "3333", 
            "Type": "non-official",
        },
        "type": "work"
    }, { 
        "address": "meganb@outlook.com",
        "id": "pqr", 
        "source": { 
            "CreatedBy": "pqr", 
            "CreatedOn": "4444", 
            "Type": "personal" 
        },
        "type": "personal" 
    } 
] 
```

- The query **MyProperty: {Profile.emails.address}** will resolve to MyProperty: “Megan.Bowen@contoso.com”.  

- If you wish to resolve all the values of the address attribute, you have to use the multi-value expansion syntax. The query **{|MyProperty:{Profile.emails.address}}** will resolve to ((MyProperty:"Megan.Bowen@contoso.com") OR (MyProperty: "meganb@hotmail.com") OR (MyProperty:"meganb@outlook.com"))  

The “|” operator should be used for resolving multi-value variables. For more examples on profile expansion refer to the table below.

| #         | Syntax |  Value returned  |
| --------- | ------ | --- |
| 1    | MyProperty:{Profile.emails.address}  |   "Megan.Bowen@contoso.com"  |
| 2 | MyProperty:{Profile.emails}   |    {Profile.emails} This will not resolve because emails are an object.|
| 3    | {?MyProperty:{Profile.emails}}  |  This will not resolve because emails is an object. The “?” operator ignores query variables that do not resolve. This variable will be removed when passed further down the query stack.   |
| 4 | {&#124;MyProperty: {Profile.emails.source.Type}}    |  ((MyProperty:"official") OR (MyProperty:"non-official") OR (MyProperty:"personal"))    |

> [!NOTE]
>
> - Profile query variables are only supported for custom verticals using a [connector](connectors-overview.md) as a content source.
> - Profile query variables are defined on the “Query” section of the [vertical set up process](customize-search-page.md#step-1-create-the-search-vertical).
> - Profile query variables is currently in preview. For more information about preview, see [Connectors preview features](connectors-overview.md#what-are-the-preview-features).

## Troubleshooting

Here's a list of common issues you might encounter and actions to fix them.

|Error  |Action  |
|---------|---------|
| I see a "Something went wrong" error message on the vertical. | Both the vertical and result types are needed to complete the setup. Make sure you have created both for the same content source. |
| I don't see my result layout, although I created one. | It takes a few minutes because these settings are generally cached. Wait for a few minutes and try again.        |
| I don't see any content sources on the vertical or result type page. | Make sure you have configured connectors and indexed data.   |

## Next steps

[Customize the results layout](customize-results-layout.md)
