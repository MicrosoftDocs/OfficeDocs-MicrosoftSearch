---
title: "Manage custom filters"
ms.author: v-revathib
author: revathi-b
manager: jeffkizn
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Manage custom filters"
---

# Manage custom filters

Filters allow users to refine the results of their queries and diplay the refined results. You can customize the filters available to your users in the Microsoft Search experience.

There are two types of filters available on the search page. 

   - Out of the box filters
   - Custom filters 
    
> [!NOTE]
> Custom Filters are currently in preview for admins and end-users in Targeted Release. For more information about preview, see [Connectors preview features](connectors-overview.md#what-are-the-preview-features).

## Out of the box filters

Out of the box filters are available by default in search verticals such as All, Files, Images, and News. On the ‘All' and ‘File' verticals, you can see the "File type" filter on the FileType property and the "Last modified" filter on the LastModifiedTime property. These filters are available in SharePoint Home, Office.com, SharePoint Sites, and Work vertical in Bing.

## Custom filters

Filters can be added to custom search verticals at the organization and site level. Refinable managed properties are used to configure filters in the vertical administration wizard.  Then a custom filter can be created inside a vertical based on a connection property. For example, you can create a Published On filter for a ServiceNow connection inside a vertical.

Filters configured for verticals in the organization scope will be available at the organization scope. Filters can be configured in the site’s scope as well.  

## To create a filter on Microsoft Search verticals at the organization level, follow these steps:

1. In [Microsoft 365 admin center](https://admin.microsoft.com/), go to [**Verticals**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/verticals)
2. Select your preferred vertical where you want to create a filter and click **Edit**.  
3. Navigate to the Filters step in the vertical's wizard.
4. Click **Add a Filter** to configure filters on refinable managed properties.
5. After adding filters, you can review and save the vertical.     

## To create a filter on Microsoft Search verticals at the site level, follow these steps:

1. In [SharePoint admin center](https://sharepoint.com/), go to Settings.
2. Look for the Microsoft Search section, and then select **Configure Microsoft Search for this site collection**.
3. In the navigation pane, go to Custom experience and then select  **Verticals**. 
4. Select your preferred vertical to create the filter and click **Edit**. 
5. Navigate to the Filters step in the vertical's wizard.
6. Click **Add a Filter** to configure filters on refinable managed properties.
7. After adding filters, you can review and save the vertical. 

## Filter across multiple properties 

Verticals may be created with one or more content sources. When a vertical is configured with multiple content sources, the refiner's properties list would show which content source each refinable property belongs to. The common managed properties will be merged based on the name (or alias) and data type. Filters can also be configured on these common properties. This is done by creating the filter on an common alias which aliases source properties across the different connections. For example you can create an **Author** filter across ServiceNow and a Jira connections by creating aliases as follows:

 | Connection | Property | Alias |
 | --- | --- | --- |
 | Service Now | Owner | Author |
 | Jira | Publisher | Author |


## Known Limitations

- Filters can only be added to custom verticals. They are not available in out of box verticals like All, Files, People, Sites, News. 
- Currently, filters are configurable on Text and DateTime properties.     
- Filters are not supported for OneDrive content. Filter values corresponding to search results from OneDrive content will not appear on filters.    
- Custom filter values will show options from SharePoint content and not from One Drive content. For example, if you create a custom filter for ‘Author’ and SharePoint content contains results only from an author, ‘Amy,’ and OneDrive content contains results only from an author called ‘John,’ the Author custom filter will show ‘Amy’ as the only      option.    
- Filter value shown from SharePoint content will be applicable to OneDrive content also.     


## Resources

[Manage verticals and result types](customize-search-page.md)
