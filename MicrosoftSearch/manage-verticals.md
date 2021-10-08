---
title: "Manage search verticals"
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
description: "Manage the search verticals on the results page"
---

# Manage search verticals

Search verticals are tabs on the search result page that show results of a specific type or from select sources. For example, the Files vertical shows results classified as files and makes it easy for users who are looking to find documents. You can customize verticals in Microsoft Search to meet the needs of your organization or individual departments.

You can manage verticals at two levels:

- **Organization level** – A vertical at the organization level appears on the search results page when users search from their [SharePoint](https://sharepoint.com/) start page, [Microsoft Office](https://office.com), and Microsoft Search in [Bing](https://bing.com)
- **Site level** – A vertical at the site level appears on the search results page when users search on a SharePoint site. For example, you might want to enable your customer service employees to search for Severity 1 incidents directly from their department’s SharePoint site.

## Understanding search verticals

Microsoft Search has two types of verticals, out of the box and custom verticals. Out of the box verticals like All, Files, and  People create easy access to the most commonly used search results.

Additional configuration options are offered on custom verticals and can be used to create the best experience for your users.

You can add search verticals that are relevant to your organization. For example, you could create a vertical for marketing-related content and another for sales, based on the type of information that each department needs. Verticals can be added to show results from content indexed by [Graph connectors](connectors-overview.md), but you can’t create a vertical for content that resides in SharePoint.

## Create search verticals

The vertical management experience is wizard driven, you're guided through steps to define the vertical's name, content source, and scope of the content to search. You can use a limited set of [Keyword Query Language (KQL)](#keyword-query-language-kql) to define the scope of vertical search for a given content source.

Following are the steps to create the custom verticals on Microsoft Search in [SharePoint home](https://sharepoint.com/), [Office](https://office.com/), or [Bing](https://bing.com/).  

### Manage organization-level verticals

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to the [**Verticals**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/verticals) page in the **Customization** section.
1. Click **add** to create a new vertical.
1. After moving through the configuration steps, you can review and save the vertical.  

### Manage site-level verticals

1. In the SharePoint site where you want to manage verticals, open the settings panel by clicking the gear.
1. Select **Site information**, and then select **View all site settings**.  
1. Look for the Microsoft Search section, and then select **Configure search settings**.
1. In the navigation pane, go to Custom experience and then select **Verticals**.
1. Click **add** to create a new vertical.
1. After setting your configuration, you can review and save the vertical.  

## View the vertical in search results

A [search result layout](manage-result-types.md) is needed for Graph connector results to render on the search vertical page. On ensuring that appropriate result layout is present, you can enable the search vertical. After you enable a vertical, there's a delay of a few hours before you can view it. You can append cacheClear=true to the URL in SharePoint and Office to view the vertical immediately. In Bing, append &features=uncachedVerticals to the work vertical URL to view the vertical immediately.

> [!NOTE]
> Added verticals aren't visible on [SharePoint](https://sharepoint.com/) and [Office](https://office.com) when viewed from mobile web browsers.

## Advanced configuration options

### Multiple connections in a vertical

A search vertical can surface results from multiple connector sources. This option provides flexibility in designing your search result page. The vertical setup process enables admins to select multiple connections in the "Content source" step.

If you accurately appoint as many *semantic labels* as possible, this experience is enhanced. You add semantic labels at the point of schema definition and ingestion. [See more about how to create and manage semantic labels](configure-connector.md#step-6-assign-property-labels).
[Here](configure-connector.md#step-6-assign-property-labels) is additional information on how to create and manage semantic labels.

> [!NOTE]
> - The multiple connections in a vertical feature is currently in preview. For more information, see [Connectors preview features](connectors-overview.md#what-are-the-preview-features).
> - A connection can be added as a content source under a single vertical. You can't use connections under multiple verticals.

To set up a query for a search vertical where multiple connection sources have been added, use common source properties to create the query.

### Keyword Query Language (KQL)

A query can be added to a vertical to narrow down results shown on the search vertical using [Keyword Query Language (KQL)](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference) (limited support). This page lists the available properties. We recommend that you use free-text keywords and property restrictions with  boolean operators for creating the KQL. Dynamic ranking operators like XRANK, proximity operators and words are not supported.

Here are some example queries.

|Scenario         | Query   |  
| --------- | ------ |
|Excluding results from archive sites           |NOT (path:http//contoso.sharepoint.com/archive OR path:http//contoso.sharepoint.com/CompanyArchive)|
| Excluding results based on file type property | NOT(FileType:htm)|  

#### Profile query variables

Use variables in the KQL query section of a vertical to provide dynamic data as an input to the query of a vertical. You can use profile query variables to make the search results contextual to the signed-in user. Profile query variables fetch values from the signed-in user’s [profile](/graph/api/resources/profile).

For example, to create a “Tickets” vertical for the user to find support tickets assigned to them, you can specify the following query in the "Query" section during the vertical creation in the administration page:  

`AssignedTo:{Profile.accounts.userPrincipalName}`

This language will narrow down the search results to show only those items for which the assignee is the user who runs the search.

[Profile resource](/graph/api/resources/profile) exposes properties as collections. For example, information related to email addresses is exposed through email collection, work positions as positions collection, and so on. All properties available in the user profile, which have AAD as the source type, are exposed as Query variables.

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
> - The profile query variables feature is currently in preview. For more information about preview, see [Connectors preview features](connectors-overview.md#what-are-the-preview-features).

## Troubleshooting

Here's a list of common problems you might encounter and actions to fix them.

|Problem  |Action  |
|---------|---------|
| I see a "Something went wrong" error message on the vertical. | Both the vertical and result types are needed to complete the setup. Make sure both are set up for the content source. |
| I don't see any content sources on the vertical page. | Make sure you have configured connectors and indexed data.   |
