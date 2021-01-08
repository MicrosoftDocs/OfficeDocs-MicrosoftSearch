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

You can use filters to customize the Microsoft Search experience. Filters let users quickly refine the set of results from their search query.

A custom filter can be created inside a vertical based on a connection property. For example, you can create a **Published On** filter for ServiceNow connection inside a vertical.

## Create a filter in an organizational level vertical

To create a filter on Microsoft search follow these steps:

1. In the Microsoft 365 admin center, go to [Verticals](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/verticals).
1. Create/Edit the vertical in which you want to create the filter
1. Navigate to the 'Filters' step in the wizard
1. Click on 'Add Filter' and get started
1. After adding filters, you can review and save the vertical.

## Things to consider

1. Additional filter capabilities exist on connection content.

    - You can also create filter on an alias to connector source properties
    - If a vertical has multiple connections, you can create a common filter across these connections. This can be done by creating the filter on an common alias which aliases source properties across across the different connections. For example you can create an **Author** filter across a ServiceNow and a Jira connection by creating aliases as follows:

    | Connection | Property | Alias |
    | --- | --- | --- |
    | Service Now | Owner | Author |
    | Jira | Publisher | Author |

1. Filters exist within the scope of a vertical.

    - If a filter is created in a vertical which is at organizational level, then the filter would only be visible at the organizational level
    - If a filter is created in a vertical which is at site level, then the filter would only be visible at the site level.

## Known Limitations

1. You can currently create filters only on string & date type managed properties.
1. You cannot create hierarchical filters.

## Resources

[Manage verticals and result types](customize-search-page.md)
