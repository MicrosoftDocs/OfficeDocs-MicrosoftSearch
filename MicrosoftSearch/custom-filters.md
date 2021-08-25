---
title: "Manage custom filters"
ms.author: rodhb
author: rodhb
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

You can use filters to customize the Microsoft Search experience. Filters let users refine the set of results from their search query and view the refined set of results.

There are two types of filters available on the search page. 

   - Out of box filters
   - Custom filters 
    
> [!NOTE]
> Custom Filters are currently in preview for admins and end-users in Targeted Release. For more information about preview, see [Connectors preview features](connectors-overview.md#what-are-the-preview-features).

## Out of box filters

Out of box filters are available by default in search verticals such as All, Files, Images, and News. On the ‘All' and ‘File' verticals, you can see the "File type" filter on the FileType property and the "Last modified" filter on the LastModifiedTime property. These filters are available in SharePoint Home, Office.com, SharePoint Sites, and Work vertical in Bing.

> [!NOTE]
> - Position of Out of Box filters is fixed.  
> - The number of filter values is limited to 50 values.  

## Custom filter

Filters can be added to custom search verticals at the organization and site level. Refinable managed properties are used to configure filters in the vertical administration wizard.  A custom filter can be created inside a vertical based on a connection property. For example, you can create a Published On filter for ServiceNow connection inside a vertical.

> [!NOTE]
> Filters configured for verticals in the organization scope will be available at the organization scope. Filters can be configured in the site’s scope as well.  

## To create a filter on Microsoft Search verticals at the organization level, follow these steps:

1. In [Microsoft 365 admin center](https://admin.microsoft.com/), go to Settings and then click **Search & Intelligence**.
2. To add a filter, click **Customizations**, and then select **Verticals**.
3. Select your preferred vertical to create the filter and click **Edit**.  
4. Navigate to the Filters step in the vertical's wizard.
5. Click **Add a Filter** to configure filters on refinable managed properties.
6. After adding filters, you can review and save the vertical.     

## To create a filter on Microsoft Search verticals at the site level, follow these steps:

1. In [SharePoint admin center](https://sharepoint.com/), go to Settings.
2. Look for the Microsoft Search section, and then select **Configure Microsoft Search for this site collection**.
3. In the navigation pane, go to Custom experience and then select  **Verticals**. 
4. Select your preferred vertical to create the filter and click **Edit**. 
5. Navigate to the Filters step in the vertical's wizard.
6. Click **Add a Filter** to configure filters on refinable managed properties.
7. After adding filters, you can review and save the vertical. 

## Filter across multiple properties 

Verticals may be created with one or more Content Sources. In the scenario where verticals are configured with multiple content sources, the refiner's properties list would show which Content Source(s) each refinable property belongs to. The common managed properties will be merged based on the Name (or alias) and data type. Filters can be configured on these common properties too. This can be done by creating the filter on an common alias which aliases source properties across the different connections. For example you can create an **Author** filter across a ServiceNow and a Jira connection by creating aliases as follows:

 | Connection | Property | Alias |
 | --- | --- | --- |
 | Service Now | Owner | Author |
 | Jira | Publisher | Author |


## Known Limitations

- Filters can only be added to custom verticals currently. They are not available in out of box verticals like All, Files, People, Sites, News. 
- Currently, filters are configurable on Text and DateTime properties.     
- Numeric filters are not supported.    
- Hierarchical filters cannot be created.
- Filters are not supported for OneDrive content. Filter values corresponding to search results from OneDrive content will not appear on filters.    
    - Custom filter values will show options from SharePoint content and not from One Drive content. For example, if you create a custom filter for ‘Author’ and SharePoint content       contains results only from an author, ‘Amy,’ and OneDrive content contains results only from an author called ‘John,’ the Author custom filter will show ‘Amy’ as the only         option.    
    - Filter value shown from SharePoint content will be applicable to OneDrive content also.     


## Resources

[Manage verticals and result types](customize-search-page.md)
