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

You can create *search verticals* and *result types* to customize the search results that users see when they search in Microsoft [SharePoint](https://sharepoint.com/), [Microsoft Office](https://office.com), and Microsoft Search in [Bing](https://bing.com). Verticals make it easier for users to find the information that they have permission to see.

For example, you could create a search vertical for marketing analysis data from third-party software for your users in the marketing department. You can also define result types and customize the layout for this data.

## About search verticals

There's a row of tabs at the top of the Microsoft Search results page. These are search verticals. A search vertical only shows results of a certain type or from a certain content set. Examples are **Files** or **News**. By default, Microsoft Search shows the verticals **All**, **People**, **Files**, **Sites**, and **News**.  

You can add search verticals that are relevant to your organization. These will appear on the Microsoft Search results page in SharePoint, Office, and Bing. For example, you could create a vertical for marketing-related content and another for sales, based on the type of information that each department needs. You can add verticals to show results only from content indexed via connectors.

You can create verticals and result types at two levels:

- **Organization level** – A vertical that you create at the organization level appears on the search results page when users search from their [SharePoint](https://sharepoint.com/) start page, on [Office](https://office.com), or on [Bing](https://bing.com).
- **Site level** – For example, you might want to enable your customer service employees to search for *Severity 1* incidents directly from their department’s SharePoint site.

### Multiple connections in a vertical

A search vertical can surface results from multiple connector sources. This option provides flexibility in designing your search result page. The vertical setup process enables admins to select multiple connections in the "Content source" step.

If you accurately appoint as many *semantic labels* as possible, this experience is enhanced. You add semantic labels at the point of schema definition and ingestion. [See more about how to create and manage semantic labels](configure-connector.md#step-5-assign-property-labels).

> [!NOTE]
> The multiple connections in a vertical feature is currently in preview. For more information, see [Connectors preview features](connectors-overview.md#what-are-the-preview-features).

A connection can be added as a content source under a single vertical. You can't use connections under multiple verticals.

To set up a query for a search vertical where multiple connection sources have been added, use common source properties to create the query.

### Before you create verticals and result types

Consider these factors:

- Make sure that the connector has been indexed. This can take up to 48 hours, depending on the file size.

- You can’t create a vertical for content that resides in SharePoint.

These are the steps to implement a vertical:

1. Create the vertical. In this step, you define the vertical’s name, content source, and scope of the content to search.
2. Define what the results for this vertical will look like.  
3. Enable the vertical (to be displayed) from the vertical list page.

## Step 1: Create the search vertical

After you start the wizard, you're guided through steps to define the vertical's name, content source, and scope of the content to search.

>[!Note]
>Verticals are created in a disabled state. You enable them to make them viewable.

You can use a limited set of [Keyword Query Language (KQL)](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference) to narrow the scope. (The properties that you can use are described later in this article.) We recommend that you use free-text keywords and property restrictions with boolean operators. KQL also supports [profile query variables](#profile-query-variables) to fine-tune results under the vertical.

### Create a vertical at the organization level

To create a vertical on Microsoft Search in SharePoint home, Office, or Bing, follow these steps:

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to [**Verticals**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/verticals).
2. Select **Add** to get started.  

### Create a vertical at the site level

1. On the [SharePoint](https://sharepoint.com/) site where you want the vertical, go to **Settings**.
2. Select **Site information**, and then select **View all site settings**.
3. Locate the **Microsoft Search** section, and then select **Configure Microsoft Search for this site collection**.
4. In the navigation pane, go to **Custom experience**, and then select the **Verticals** tab.
5. To add a vertical, select **Add**. Or to edit a vertical, select it from the list.

## Step 2: Create result types

You can use *result types* to define how results are displayed in the vertical. The result layout lets you show important information directly in the search results, so users don't have to select each result to see if they found what they're looking for.

### Default search result layout

A default search result layout will be shown for connector content if the *labels* and *content* properties were correctly mapped to the source properties when the connector was configured. The *title* label is the most important label. We *strongly* recommend that you have a property assigned to this label to use the default search result layout.

### Create your own result type

To create your own search result layout and override the default search result layout, you create a *result type*. A search result type is a rule that causes distinct kinds of search results to be displayed in different ways. It consists of:

- **One or more conditions** to compare each search result against, such as the content source of the search result.  
- A **result layout** to use for search results that meet the conditions. The resulting layout controls how the results that meet the conditions appear and behave on a search results page.

*If you don't do appropriate mapping to show default search result layout, you must create at least one result type for results to display on the vertical.* 

You can create multiple result types for each vertical, which allows you to use different layouts for different type of results. For example, you might customize *Severity 1* incidents to have more prominent colors and a larger font than *Severity 3* incidents.

After you start the wizard, you're guided through the steps to define the name, content source, and conditions for the result type. You can define the priority of the result type from the list view.
  
### Create a result type at the organization level

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to [**Result types**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/resulttypes).
2. To add a result type, select **Add**. To edit a result type, select the result type from the relevant list.

### Create a result type at the site level

1. On the [SharePoint](https://sharepoint.com/) site where you want the result type, go to **Settings**.
2. Select **Site information**, and then select **View all site settings**.
3. Look for the **Microsoft Search** section, and then select **Configure Microsoft Search for this site collection**.
4. In the navigation pane, go to **Custom experience**, and select the **Result type** tab.
5. To add a result type, select **Add**.  Or, to edit a result type, select the result type in the list.

## Step 3: View the vertical after it's enabled

After you enable the vertical, there's a delay of a few hours before you can view it. But you can append `cacheClear=true` to the URL in SharePoint and Office to view the vertical immediately. For Bing, append `&features=uncachedVerticals` to the `Work vertical URL` to view the vertical immediately.

> [!NOTE]
> Added verticals aren't visible on SharePoint](https://sharepoint.com/) and [Office](https://office.com) when viewed from mobile web browsers.

## Profile query variables

Use variables in the KQL query section of a vertical to provide dynamic data as an input to the query of a vertical. You can use profile query variables to make the search results contextual to the signed-in user. Profile query variables fetch values from the signed-in user’s [profile](/graph/api/resources/profile).

For example, to create a “Tickets” vertical for the user to find support tickets assigned to them, you can specify the following query in the "Query" section during the vertical creation in the administration page:  

`AssignedTo:{Profile.accounts.userPrincipalName}`

This language will narrow down the search results to show only those items for which the assignee is the user who runs the search.

[Profile resource](/graph/api/resources/profile?view=graph-rest-beta) exposes properties as collections. For example, information related to email addresses is exposed through email collection, work positions as positions collection, and so on. All properties available in the user profile, which have AAD as the source type, are exposed as Query variables.


Consider a user who has three email addresses available in the email collection, as shown here:

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

- The query `MyProperty: {Profile.emails.address}` will resolve to *MyProperty: “Megan.Bowen@contoso.com”*.  

- To resolve all the values of the address attribute, use the multi-value expansion syntax. The query `{|MyProperty:{Profile.emails.address}}` will resolve to *((MyProperty:"Megan.Bowen@contoso\.com")* or *(MyProperty: "meganb@hotmail\.com")* or  *(MyProperty:"meganb@outlook\.com"))*.

Use the “|” operator to resolve multi-value variables. See the following table for more examples of profile expansion.

| #         | Syntax |  Value returned  |
| --------- | ------ | --- |
| 1    | MyProperty:{Profile.emails.address}  |   "Megan\.Bowen@contoso.com"  |
| 2 | MyProperty:{Profile.emails}   |    {Profile.emails} This won't resolve because *emails* is an object.|
| 3    | {?MyProperty:{Profile.emails}}  |  This won't resolve because *emails* is an object. The “?” operator ignores query variables that don't resolve. This variable will be removed when passed further down the query stack.   |
| 4 | {&#124;MyProperty: {Profile.emails.source.Type}}    |  ((MyProperty:"official") or (MyProperty:"non-official") or (MyProperty:"personal"))    |

> [!NOTE]
>
> - Profile query variables are only supported for custom verticals that use a [connector](connectors-overview.md) as a content source.
> - Profile query variables are defined in the “Query” section of the [vertical setup process](customize-search-page.md#step-1-create-the-search-vertical).
> - The profile query variables feature is currently in preview. For more information about preview, see [Connectors preview features](connectors-overview.md#what-are-the-preview-features).

## Troubleshooting

Here's a list of common problems you might encounter and actions to fix them.

|Problem  |Action  |
|---------|---------|
| I see a "Something went wrong" error message on the vertical. | Both the vertical and result types are needed to complete the setup. Make sure you created both for the same content source. |
| I don't see my result layout, although I created one. | There may be a delay of a few minutes because these settings are cached. Wait a few minutes and try again.        |
| I don't see any content sources on the vertical or result type page. | Make sure you have configured connectors and indexed data.   |

## Next steps

[Customize the results layout](customize-results-layout.md)
