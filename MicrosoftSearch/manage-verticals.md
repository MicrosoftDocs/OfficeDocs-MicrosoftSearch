---
title: "Manage search verticals"
ms.author: jypal
author: jypal6
manager: bstucker
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
ms.date: 03/15/2022
search.appverid:
- BFB160
- MET150
- MOE150
description: "Manage the search verticals on the results page"
---

# Manage search verticals

Search verticals are tabs on the search result page that show results of a specific type or from select sources. For example, the Files vertical shows results classified as files and makes it easy for users who are looking to find documents. You can customize verticals in Microsoft Search to meet the needs of your organization or individual departments. Microsoft Search has two types of verticals, out of the box or default and custom verticals. The default verticals, such as All, Files, and People, create easy access to the most commonly used search results.

You can manage verticals at two levels:

- **Organization level** – A vertical at the organization level appears on the search results page when users search from their [SharePoint](https://sharepoint.com/) start page, [Microsoft Office](https://office.com), and Microsoft Search in [Bing](https://bing.com)
- **Site level** – A vertical at the site level appears on the search results page when users search on a SharePoint site. For example, you might want to enable your customer service employees to search for Severity 1 incidents directly from their department’s SharePoint site.

## Default verticals

Default verticals are present at the organization level in experiences like [SharePoint](https://sharepoint.com/), [Microsoft Office](https://office.com/), and Microsoft Search in [Bing](https://bing.com/) or at the SharePoint site level in each site's search result page. 

Here's a summary of customization capabilities on out of the box verticals.

|Customization type   |Organization level     |Site level   |
|---------|---------|---------|
| Rename vertical    | Yes |Yes  |
| Disable vertical   | Partial       |Yes  |
| Adding a query      | Partial       |Yes  |

## Custom verticals
You can add search verticals in search experience at Organization or site level search for content from Graph connectors or SharePoint. Custom verticals for SharePoint content will show results from the respective scope, similar to the other verticals at that scope. For example, a custom vertical at the Organization scope will show all results, while a custom vertical with SharePoint content in the Marketing site will show data from that site. The same is true for hub sites where the same hub scope will be applied. 

## Create or modify search verticals

The vertical management experience is wizard driven, you're guided through steps to define the vertical's name, content source, and scope of the content to search. You can use a limited set of [Keyword Query Language (KQL)](#keyword-query-language-kql) to define the scope of the vertical search for a given content source. Filters can also be added to out of box and custom verticals at the organization and site level. For more information about filters, see [Manage filters](/microsoftsearch/custom-filters).

### Manage organization-level verticals

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to the [**Verticals**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/verticals) page in the **Customization** section.
1. Select an existing vertical and click **edit** or click **add** to create a new vertical.
1. After moving through the configuration steps, you can review and save the vertical.  

### Manage site-level verticals

1. In the SharePoint site where you want to manage verticals, open the settings panel by clicking the gear.
1. Select **Site information**, and then select **View all site settings**.  
1. Look for the Microsoft Search section, and then select **Configure search settings**.
1. In the navigation pane, go to Custom experience and then select **Verticals**.
1. Select an existing vertical and click **edit** or click **add** to create a new vertical.
1. After setting your configuration, you can review and save the vertical.  

## View the vertical in the search result page

A [search result layout](manage-result-types.md) is needed for Graph connector results to render on the search vertical page. On ensuring that appropriate result layout is present, you can enable the search vertical. After you enable or update a vertical, there's a delay of a few hours before you can view the changes on the search page. You can append cacheClear=true to the URL in SharePoint and Office to view the changes immediately. In Bing, append &features=uncachedVerticals to the work vertical URL to view the changes immediately.

> [!NOTE]
> Added verticals aren't visible on [SharePoint](https://sharepoint.com/) and [Office](https://office.com) when viewed from mobile web browsers.

## Advanced configuration options

### Multiple connections in a vertical

A search vertical can surface results from multiple connector sources. This option provides flexibility in designing your search result page. The vertical setup process enables admins to select multiple connections in the "Content source" step.

If you accurately appoint as many *semantic labels* as possible, this experience is enhanced. You add semantic labels at the point of schema definition and ingestion. [See more about how to create and manage semantic labels](configure-connector.md#step-6-assign-property-labels).
[Here](configure-connector.md#step-6-assign-property-labels) is additional information on how to create and manage semantic labels.

> [!NOTE]
> - A connection can be added as a content source under a single vertical. You can't use connections under multiple verticals.

To set up a query for a search vertical where multiple connection sources have been added, use common source properties to create the query.

### Keyword Query Language (KQL)

A query can be added to a vertical to narrow down results shown on the search vertical using [Keyword Query Language (KQL)](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference) (limited support). This page lists the available properties. We recommend that you use free-text keywords and property restrictions with  boolean operators for creating the KQL. Dynamic ranking operators like XRANK, proximity operators and words aren't supported.

Here are some example queries.

|Scenario         | Query   |  
| --------- | ------ |
|Excluding results from archive sites           |NOT (path:http//contoso.sharepoint.com/archive OR path:http//contoso.sharepoint.com/CompanyArchive)|
| Excluding results based on file type property | NOT(FileType:htm)|  

Use variables in the KQL query section of a vertical to provide dynamic data as an input to the query of a vertical. "Profile" and "query string" are the types of query variables that can be used.

#### Profile query variables

You can use profile query variables to contextualize the search results to the signed-in user. Profile query variables fetch values from the signed-in user’s [profile](/graph/api/resources/profile). For example, to create a “Tickets” vertical for the user to find support tickets assigned to them, you can specify the following query in the “Query” section during the vertical creation in the administration page.

`AssignedTo:{Profile.accounts.userPrincipalName}`

This will trim the search results to show only items that are assigned to the person doing the search.

[Profile resource](/graph/api/resources/profile) exposes properties as collections. For example, information related to email addresses is exposed through email collection, work positions as positions collection, and so on. All properties available in the user profile are exposed as Query variables.

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

- To resolve all the values of the address attribute, use the multi-value expansion syntax. The query `{|MyProperty:{Profile.emails.address}}` will resolve to *((MyProperty:"Megan.Bowen@contoso\.com")* OR *(MyProperty: "meganb@hotmail\.com")* OR  *(MyProperty:"meganb@outlook\.com"))*.

Use the “|” operator to resolve multi-value variables. See the following table for more examples of profile expansion.

| #         | Syntax |  Value returned  |
| --------- | ------ | --- |
| 1    | MyProperty:{Profile.emails.address}  |   "Megan\.Bowen@contoso.com"  |
| 2 | MyProperty:{Profile.emails}   |    {Profile.emails} This won't resolve because *emails* is an object.|
| 3    | {?MyProperty:{Profile.emails}}  |  This won't resolve because *emails* is an object. The “?” operator ignores query variables that don't resolve. This variable will be removed when passed further down the query stack.   |
| 4 | {&#124;MyProperty: {Profile.emails.source.Type}}    |  ((MyProperty:"official") OR (MyProperty:"nonofficial") OR (MyProperty:"personal"))    |

#### Query String variables

Query String variables enable you to personalize search results based on how users interact with SharePoint sites. This is done by adding key-value pairs to the search URL. For example, suppose you have a SharePoint site that provides information on a project with a simple web part that shows in-progress tasks. Clicking on the "In-progress" web part, links users to the "Work items" search vertical, where the results are refined to show only items tagged as **InProgress**.

This can be done by specifying the following query in the “Query” section during vertical creation in the administration page.

`Status:{QueryString.state}`

The URL on the SharePoint site button web part needs to be updated to pass the following key value pair https://{your-domain}.sharepoint.com/sites/{site-name}/_layouts/15/search.aspx/{vertical-ID}?state=InProgress

The query status:{QueryString.state} will resolve to status:InProgress.

Here are more examples of query string expansion.

| #         | Query Syntax | URL Syntax | Value returned |
| --------- | --------- | --------- | --------- |
| 1    | MyProperty:{QueryString.state}  |   https://{your-domain}.sharepoint.com/sites/{site-name}/_layouts/15/search.aspx/{vertical-ID}?state=InProgress  |   MyProperty:InProgress  |
| 2 | MyProperty:{QueryString.state} OR MyProperty:{QueryString.priority}   |    https://{your-domain}.sharepoint.com/sites/{site-name}/_layouts/15/search.aspx/{vertical-ID}?state=InProgress&priority=1 |   MyProperty:InProgress OR MyProperty:1  |
| 3    | {?MyProperty:{QueryString.state}}  |  https://{your-domain}.sharepoint.com/sites/{site-name}/_layouts/15/search.aspx/{vertical-ID}?State=InProgress   |   Here state won't resolve because QueryStrings are case sensitive.  The “?” operator ignores query variables that don't resolve. This variable will be removed when passed further down the query stack.  |
| 4 | {\|MyProperty: {QueryString.state}}    |  https://{your-domain}.sharepoint.com/sites/{site-name}/_layouts/15/search.aspx/{vertical-ID}?state=InProgress,Closed    |   (MyProperty:InProgress) OR (MyProperty:Closed)  <br /> The \| operator is used to resolve muti-value variables. The values for the variables should be passed using the comma separator as shown in the URL syntax. |
| 5 | {MyProperty: {QueryString.state}}    |  https://{your-domain}.sharepoint.com/sites/{site-name}/_layouts/15/search.aspx/{vertical-ID}?state=InProgress,Closed   |   MyProperty:InProgress <br /> Here only the first value of state gets picked up from the URL since the query syntax doesn't define it as a multi-value variable. |


## Limitations
- Language localization isn't applicable to names of out of box verticals once modified. 
- Custom verticals don't appear on the mobile view of Microsoft Search. 
- Adding query isn't supported on the People vertical. 
- Vertical modification and new verticals aren't visible to guest users in an organization. 
- Vertical re-ordering isn't supported.
- Vertical renaming for All tab isn't supported in Microsoft Search in Bing.
- Query string variables can only be used in SharePoint sites.

## Troubleshooting

Here's a list of common problems you might encounter and actions to fix them.

|Problem  |Action  |
|---------|---------|
| I see a "Something went wrong" error message on the vertical. | Both the vertical and result types are needed to complete the setup. Make sure both are set up for the content source. |
| I don't see any content sources on the vertical page. | Make sure you have configured connectors and indexed data.   |


