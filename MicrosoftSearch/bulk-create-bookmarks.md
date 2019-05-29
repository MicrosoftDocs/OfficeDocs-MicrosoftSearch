---
title: "Bulk create bookmarks"
ms.author: dawholl
author: dawholl
manager: kellis
ms.date: 09/11/2018
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
ms.assetid: def300e7-103c-4e92-a062-28ffa27561d7
ROBOTS: NOINDEX
description: "Create lots of bookmarks at once with import tools for the Microsoft Search Admin portal"
---

# Bulk create bookmarks

> [!IMPORTANT]
> This article applies to the Microsoft Search in Bing admin portal. We’re moving the portal to the Microsoft 365 admin center, and then it will be removed. We recommend that you use the Microsoft 365 admin center to get started. [Overview of Microsoft Search](overview-microsoft-search.md).
    
Download and use the .csv template to bulk create, edit, and save bookmarks. To bulk edit existing bookmarks, export them from the Admin portal, make the necessary edits, and then import them.
  
1. In the upper-right corner of the Bookmarks section, click **Import**
    
2. Click **Download bookmarks template (.csv)**
    
3. Save and open the .csv file
    
4. Add the bookmark content and settings and save the file

    The .csv file should be saved as a CSV UTF-8 file, other file types and or encodings may cause import errors
    
5. In the upper-right corner of the Bookmarks section, click **Import**
    
6. In the Import bookmarks pane, click **Browse** and navigate to the .csv file you want to import 
    
7. Click **Import**

# Prevent import errors      
You'll get an error if any required data is missing or invalid. Depending on the error, a log file may be generated with more information about the rows and columns that need to be corrected. Make any necessary edits, and try importing the file again.

> [!NOTE]
> Until all errors are resolved, you can't create or edit any bookmarks. 

To help prevent errors, make sure your import file is properly formatted:
- Includes the header row that was in the import template
- Includes all columns that were in the import template
- The column order is the same as the import template
- These columns can be empty: Id, Last Modified, and Last Modified By
- The State column can't be empty, this information is required  
Based on the State field, bookmarks will be saved as draft, suggested, scheduled, or they will be published automatically.

Also, if you include the Id of an existing bookmark, it will be replaced with the information in the import file.

For organizations with mulitple tenants, you can export your bookmarks from one tenant and import it into another. But you must remove all of the data in the Id column before you import.

To find out more about required and recommended fields, see [Create bookmarks](create-bookmarks.md).
