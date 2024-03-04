---
title: "Manage locations"
ms.author: davidedwards
author: dawholl
manager: kellis
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
ms.assetid: 8ab9aa00-cd74-405f-8410-9a1c3cfacdb9
description: "Over time, you may need to update a location's status and content to keep it relevant."
ms.date: 01/08/2019
---

# Manage locations

## Location

Location helps your users find addresses and locate your organization's buildings by providing an accurate location for offices, campuses, and buildings, along with directions and navigation. Administrators should add all important locations of your organization. Unlike Bookmarks and Q&A, the index isn't refreshed immediately, and it can take several hours for new or changed locations to appear in search results.

### Add or edit a single location

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to [**Locations**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/locations)
1. To add a new location, select **Add**.
1. To edit a location, select the location in the relevant locations list.
1. As you add or edit the information, the preview automatically updates.
1. Save your changes.

### Bulk add or edit locations

Administrators can use the Import or Export feature to bulk add or edit locations.

Use the import/export feature to:

1. Bulk add location - Add details in the location template file, and then import it.
1. Bulk edit locations - Export locations to a .csv file, then edit the location details in the exported .csv file, and then import the updated .csv file.
1. Backup locations – Export existing locations to a .csv file.

To export or import locations:

1. In the upper-right corner of the **Locations** tab, select **Import**.
Select **Export** to download the existing locations in a .csv file.
1. In the right pane, choose the option to import using a .csv file.
Download the template file for a list of the required fields and details.
1. Add or edit location details in the template file, and then save it on your computer.
1. In the **Import** locations pane, select **Browse**, and then the .csv file that you want to import.
1. Select **Import**.

Here are some important points regarding the template file:

- Never edit data in these fields: *Id*, *Last Modified*, and *Last Modified By*
- If you include the *Id* of an existing location, it's replaced with the information in the import file.
- Not all fields in the template file are required and required fields vary depending on the location state.
- Based on the *State* field, locations are saved as draft, suggested, scheduled, or they're published automatically.
- For partners who manage multiple organizations, you can export your locations from one org and import them into another. But you must remove the data in the *Id* column before you import.

> [!NOTE]
> You cannot import Locations if there are any errors in the template file. To prevent errors, make sure your import file is properly formatted and include all the required information.

For more information on how to prevent error, see [Prevent import errors](manage-bookmarks.md#prevent-import-errors).
