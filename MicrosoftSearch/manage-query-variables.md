--- 
title: "Manage Query Variables" 
ms.author: anvalsan 
author: anvalsan 
manager: jeffkizn 
ms.audience: Admin 
ms.topic: article 
ms.service: mssearch 
localization_priority: Normal 
search.appverid: 
- BFB160 
- MET150 
- MOE150 
description: "Managing query variables for verticals" 
--- 

# Profile Query variables

Query variables are used in KQL query section of a vertical to provide dynamic data as an input to the query of a vertical.

Profile query variables fetch values from the signed-in user’s [profile](https://docs.microsoft.com/graph/api/resources/profile?view=graph-rest-beta). You can use profile query variables to make the search results contextual to the signed-in user. For example, adding the following query template will narrow down the search results to show only those items where the author is the user performing the search.

**Author**: {Profile.accounts.userPrincipalName}
[Profile resource](https://docs.microsoft.com/graph/api/resources/profile?view=graph-rest-beta) exposes properties as collections. For example, information related to email addresses is exposed through email collection, work positions as positions collection and so on. All properties available in the user profile as exposed as Query variables.
**Syntax**: Profile.<Relationship.Property.PropertyName>
Guidelines to be followed for invoking profile attributes. A typical structure of a profile resource is given below.
```JSON
    Profile {
        Collection1: {},
        Collection2: {
            Property1:”abcd1234”
            Property2: {
                Property2.1:
                Property2.2:{
                    Property 2.2.1:
                    Property 2.2.2:}}}}
```

Only single value variables will be expanded and not the entire collection object. For instance, _{Profile.Collection2.Property2}_ will not expand since it's an object. _{Profile.Collection2.Property1}_ will return “abcd1234” since it contains a single value property. The path pointed by the Query variable should resolve to a single value entity.

Multiple instances for a collection will be expanded depending on the syntax used. For example, consider a user who has 3 email addresses available in the email collection.
```JSON
emails:
    {
        {
            address: [Megan.Bowen@contoso.com](”Megan.Bowen@contoso.com”)
            id: “xyz”
            source:{  
                CreatedBy:”xyz”  
                CreatedOn:”2222”  
                Type:” aad”  
                    }  
            type:”main”  
            },  
            {  
            address:”meganb@hotmail.com”  
            id: “abc”  
            source:{  
                CreatedBy:”abc”  
                CreatedOn:”3333”  
                Type:” non-official”  
                    }  
            type:”work”  
            },  
            {  
            address:”meganb@outlook.com”  
            id: “pqr”  
            source:{  
                CreatedBy:”pqr”  
                CreatedOn:”4444”  
                Type:” personal”
                    }  
            type:”personal”  
        }  
    }
```

{&#124;MyProperty:{Profile.emails.address}} will return -
((MyProperty:"Megan.Bowen@contoso.com") OR (MyProperty:"meganb@hotmail.com") OR (MyProperty:"meganb.outlook.com"))

MyProperty:{Profile.emails.address} will return -
MyProperty:Megan.Bowen@contoso.com")

The “&#124;” operator should be used for expanding multi-value variables.  

For more examples on Profile expansion, please refer to the table below.

| #         | Syntax |  Value returned post   |
| --------- | ------ | --- |
| 1    | MyProperty: {Profile.emails.address}  |   "Megan.Bowen@contoso.com"  |
| 2 | MyProperty:{Profile.emails}   |    {Profile.emails} This will not resolve because emails is an object.|
| 3    | {?MyProperty:{Profile.emails}} |  This will not resolve because emails is an object. The “?” operator ignores query variables that does not resolve. This variable will be removed when passed further down the query stack.   |
| 4 | {&#124;MyProperty: {Profile.emails.source.Type}}    |  ((MyProperty:”aad”) OR (MyProperty:”non-official”) OR (MyProperty:”personal”))    |

## **Note**

- Profile query variables are only supported for custom verticals using a [connector](https://docs.microsoft.com/microsoftsearch/connectors-overview) as a content source.
- Profile query variables are defined on the “Query” section of the [vertical set up process](https://docs.microsoft.com/microsoftsearch/customize-search-page#step-1-create-the-search-vertical).
- Profile query variables is currently in preview. For more information about preview, see [Connectors preview features](https://docs.microsoft.com/microsoftsearch/connectors-overview#what-are-the-preview-features).
