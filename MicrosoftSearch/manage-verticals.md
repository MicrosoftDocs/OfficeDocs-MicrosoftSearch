---
title: "Manage search verticals"
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
description: "Manage the search verticals on the results page"
---

# Search verticals
Search verticals are tabs on the search result page showing results of a certain type or from a certain content source. For example, Files vertical shows results classified as files and makes it easy for users who are looking to find documents.

## You can create verticals at two levels:
- **Organization level** – A vertical that you create at the organization level appears on the search results page when users search from their SharePoint start page, on Office, or on Bing. 
- **Site level** – For example, you might want to enable your customer service employees to search for Severity 1 incidents directly from their department’s SharePoint site. 

### There are two types of verticals
1. Out of box verticals
2. Custom verticals

### Out of box verticals
By default, Microsoft Search shows the list of verticals All, People, Files, etc. these are called Out of box verticals. These verticals are present at the Organization level in experiences like SharePoint Home, Office.com, and Microsoft search in Bing or at the Site level in the respective site search result page.

Here is a summary of customization capabilities on out of box verticals.
|Customization  type          | Organization level    |  Site level    |
| --------- | ------ | --- |
|Rename vertical      |Yes     |   Yes     |
| Disable vertical  | Partial (Only for Site, News)     |    Yes|
|Adding query       | Partial    |  Yes     |

### Custom verticals
You can add search verticals that are relevant to your organization. These will appear on the Microsoft Search results page in SharePoint, Office, and Bing. For example, you could create a vertical for marketing-related content and another for sales, based on the type of information that each department needs.  
You can add verticals to show results from content indexed via connectors or from SharePoint. 

> [!NOTE]
> Adding verticals for SharePoint content source is available to Targeted release customers. 

## Create the search vertical
After you start the wizard, you're guided through steps to define the vertical's name, content source, and scope of the content to search. 

You can use a limited set of Keyword Query Language (KQL) to narrow the scope. (The properties that you can use are described later in this article.) We recommend that you use free-text keywords and property restrictions with Boolean operators. KQL also supports profile query variables to fine-tune results under the vertical. 

Following are the steps to modify the out of box verticals or create the custom verticals on Microsoft Search in [SharePoint home](https://sharepoint.com/), [Office](https://office.com/), or [Bing](https://bing.com/).  

### Organization level navigation
1. In the [Microsoft 365 admin center](https://admin.microsoft.com/), go to Settings and then click **Search & Intelligence**.
2. Click **Customization** and then select **Verticals**.  

**Modify an Out of box vertical**
1. The out of box verticals will be visible. Select your preferred Out of box vertical to modify and click **Edit**. 
2. After modifying a vertical, you can review and save the vertical.   

**Create a custom vertical**
1. Select **Add** to get started.
2. After adding a vertical, you can review and save the vertical.  

### Site level navigation
1. On the [SharePoint admin center](https://sharepoint.com/), go to Site Settings.  
2. Look for the Microsoft Search section, and then **select Configure Microsoft Search for this site collection**.
3. In the navigation pane, go to Custom experience and then select **Verticals**.    

**Modify an Out of box vertical**
1. The out of box verticals will be visible. Select your preferred Out of box vertical to modify and click **Edit**. 
2. After modifying a vertical, you can review and save the vertical. 

**Create a custom vertical**
1. Select **Add** to get started.
2. After adding a vertical, you can review and save the vertical.  

## View the vertical after it's enabled
After you enable the vertical, there's a delay of a few hours before you can view it. But you can append cacheClear=true to the URL in SharePoint and Office to view the vertical immediately. For Bing, append &features=uncachedVerticals to the Work vertical URL to view the vertical immediately. 

> [!NOTE]
> Added verticals aren't visible on SharePoint and Office when viewed from mobile web browsers. 

## Multiple connections in a vertical

A search vertical can surface results from multiple connector sources. This option provides flexibility in designing your search result page. The vertical setup process enables admins to select multiple connections in the "Content source" step.

If you accurately appoint as many *semantic labels* as possible, this experience is enhanced. You add semantic labels at the point of schema definition and ingestion. [See more about how to create and manage semantic labels](configure-connector.md#step-6-assign-property-labels).
[Here](configure-connector.md#step-6-assign-property-labels) is additional information on how to create and manage semantic labels.

> [!NOTE]
> - The multiple connections in a vertical feature is currently in preview. For more information, see [Connectors preview features](connectors-overview.md#what-are-the-preview-features).
> - A connection can be added as a content source under a single vertical. You can't use connections under multiple verticals.

To set up a query for a search vertical where multiple connection sources have been added, use common source properties to create the query.

## Keyword Query Language (KQL)
A query can be added to a vertical to narrow down results shown on the search vertical using [Keyword Query Language (KQL)](https://docs.microsoft.com/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference) (limited support).   This page lists the available properties. We recommend that you use free-text keywords and property restrictions with Boolean operators for creating the KQL.   

A few examples of queries are:
- Excluding results from sites    
- The following query will filter out data from the Archive site
  - NOT (path:http//contoso.sharepoint.com/archive OR path:http//contoso.sharepoint.com/CompanyArchive)    
  - Excluding results based on certain properties.    
- The following query removes results with file type ‘htm’ from search results page NOT(FileType:htm)    

The following aspects of KQL are not supported at present:
- Dynamic ranking operator:    
  - XRANK    
  - Proximity operator and words    
- Query variables   

## Profile query variables

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
> - Profile query variables are defined in the “Query” section of the [vertical setup process](customize-search-page.md#step-1-create-the-search-vertical).
> - The profile query variables feature is currently in preview. For more information about preview, see [Connectors preview features](connectors-overview.md#what-are-the-preview-features).

### Known Limitations
- Out of the box and new verticals order cannot be changed.   
- If the name of an out of the box vertical is edited, language localization will no longer apply to vertical names.    
- KQL does not apply to content surfaced from user OneDrive.    
- Custom verticals do not appear on the mobile view of Microsoft search.    
- Adding query is not supported on the People vertical. 
- Vertical modification and new verticals are not visible to guest users in an organization.   

## Troubleshooting

Here's a list of common problems you might encounter and actions to fix them.

|Problem  |Action  |
|---------|---------|
| I see a "Something went wrong" error message on the vertical. | Both the vertical and result types are needed to complete the setup. Make sure you created both for the same content source. |
| I don't see my result layout, although I created one. | There may be a delay of a few minutes because these settings are cached. Wait a few minutes and try again.        |
| I don't see any content sources on the vertical or result type page. | Make sure you have configured connectors and indexed data.   |
