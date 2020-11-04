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

# Create custom Filters

You can create filters to customize the search experience that users see when they search in Microsoft [SharePoint](https://sharepoint.com/), Microsoft [Office](https://office.com), and Microsoft Search in [Bing](https://bing.com). Filters lets users quickly refine the set of results from their search query.

A custom filter can be created inside a vertical based on a connection property. For example, you can create a **Published On** filter for ServiceNow connection inside a custom vertical.

## Things to consider

1. For creating custom filter on connection content source, some additional capabilities are provided:
- You can also create filter on an alias to connector source properties
- In case your vertical has multiple connections then you can create a common filter across these connections. This can be done by creating the filter on an common alias which aliases source properties across across different connections. For example you can create an **Author** filter across a ServiceNow & a Jira connection by creating aliases as follows:

| Connection | Property | Alias |
| --- | --- | --- |
| Service Now | Owner | Author |
| Jira | Publisher | Author |

2. Filters exist within the scope of the vertical. Hence,  
- If a filter is created in a vertical which is at organizational level, then the filter would only be visible at the organizational level
- If a filter is created in a vertical which is at site level, then the filter would only be visible at the site level.

## Steps to Create custom filter

### Create filter in organizational level vertical:

To create a filter on Microsoft search follow these steps:

1. In the Microsoft 365 admin center, go to Settings > Microsoft Search > Customization > Verticals.
2. Create/Edit the vertical in which you want to create the filter
3. Navigate to the ‘Filters’ step in the wizard
4. Click on ‘Add Filter’ and get started
After adding filters, you can review and save the vertical.

## Known Limitations

1. You can currently create filters only on String & Date type managed properties. 
2. You cannot create hierarchical filters

## Resources

[Customize search result page](customize-search-page.md)