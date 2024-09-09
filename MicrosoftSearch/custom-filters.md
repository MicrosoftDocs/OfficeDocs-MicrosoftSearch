---
title: "Manage  filters"
ms.author: misvenso
author: revathi-b
manager: wobba
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
ms.date: 11/22/2021
search.appverid:
- BFB160
- MET150
- MOE150
description: "Manage filters for use on the SERP"
---

# Manage filters

Filters allow users to refine the results of their queries and display the refined results. You can customize the filters available to your users in the Microsoft Search experience.

There are three types of filters available on the search page.

- Out of the box filters
- Content source filters
- Custom filters

## Out of the box filters

Out of the box filters are available by default in search verticals such as All, Files, Images, and News. On the ‘All' and ‘File' verticals, you can see the "File type" filter on the FileType property and the "Last modified" filter on the LastModifiedTime property. These filters are available in SharePoint Home, Office.com, SharePoint Sites, and Work vertical in Bing.

## Content source filters 

If you have multiple content sources enabled in Microsoft Search, you can also see the content source filter in the “All” vertical. These sources can be SharePoint-OneDrive, Power BI, Viva Learning, or sources added using Graph Connectors. 
You can customize how Graph Connector content sources are shown in the filter experience. To customize the name and icon shown to users for a connection in content source filters: 
- In Microsoft 365 admin center, go to Search and Intelligence > Data sources > select the connection you want to customize and then select Edit in the side panel. 
- Set your Connection Display name and icon. Certain keywords are reserved and can’t be used in the Display name (such as Microsoft brands and default search vertical names). 
To group together multiple connections into a single value in the filter, set the same Display name for them.

## Custom filters

Filters can be added to custom search verticals at the organization and site level. Refinable managed properties are used to configure filters in the vertical administration wizard.  Then a custom filter can be created inside a vertical based on a connection property. For example, you can create a Published On filter for a ServiceNow connection inside a vertical.

Filters configured for verticals in the organization scope will be available at the organization scope. Filters can be configured in the site’s scope as well.  

## Create organization level filters

1. In [Microsoft 365 admin center](https://admin.microsoft.com/), go to [**Verticals**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/verticals)
1. Select your preferred vertical where you want to create a filter and click **Edit**.  
1. Navigate to the Filters step in the vertical's wizard.
1. Click **Add a Filter** to configure filters on refinable managed properties.
1. After adding filters, you can review and save the vertical.

## Create SharePoint site level filters

1. In the SharePoint site where you want to manage verticals, open the settings panel by clicking the gear.
1. Select **Site information**, and then select **View all site settings**.  
1. Look for the Microsoft Search section, and then select **Configure search settings**.
1. In the navigation pane, go to Custom experience under Microsoft Search and then select  **Verticals**.
1. Select your preferred vertical to create the filter and click **Edit**.
1. Navigate to the Filters step in the vertical's wizard.
1. Click **Add a Filter** to configure filters on refinable managed properties.
1. After adding filters, you can review and save the vertical.

## Filter across multiple properties

Verticals may be created with one or more content sources. When a vertical is configured with multiple content sources, the refiner's properties list shows which content source each refinable property belongs to. The common managed properties will be merged based on the name (or alias) and data type. Filters can also be configured on these common properties. This is done by creating the filter on a common alias which aliases source properties across the different connections. For example you can create an **Author** filter across ServiceNow and Jira connections by creating aliases as follows:

 | Connection | Property | Alias |
 | --- | --- | --- |
 | Service Now | Owner | Author |
 | Jira | Publisher | Author |

## Important Details

- Filters are configurable on Text and DateTime properties.
- A filter will show a maximum of 50 values in the drop-down.
- The order of out of the box filters cannot be adjusted.
- Filters are not supported for OneDrive content. Filter values corresponding to search results from OneDrive content will not appear on filters.
- Custom filter values will show options from SharePoint content and not from One Drive content. For example, if you create a custom filter for ‘Author’ and SharePoint content contains results only from an author, ‘Amy,’ and OneDrive content contains results only from an author called ‘John,’ the Author custom filter will show ‘Amy’ as the only      option.
- A filter value shown for SharePoint content will apply to OneDrive content when used.
