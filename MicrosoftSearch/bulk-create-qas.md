---
title: "Bulk create Q&As"
ms.author: dawholl
author: dawholl
manager: kellis
ms.date: 12/18/2018
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
ms.assetid: 7bada218-8908-4956-aae3-6ffaeef384ca
description: "Quickly add answers to frequently asked questions with import tools in the Microsoft Search Admin portal"
---

# Bulk create Q&As

> [!IMPORTANT]
> Microsoft Search in Bing settings are now available in the Microsoft 365 admin center. Get started by [assigning search admins](https://docs.microsoft.com/en-us/microsoftsearch/setup-microsoft-search#step-2-assign-search-admin-and-search-editor) in your admin center.

Download and use the .csv template to bulk create or bulk edit Q&As. It's also a simple way to bulk save draft Q&As that need additional edits or updates. If you need to bulk edit existing Q&As, export them from the Admin portal, make the necessary edits, and then import them.
  
1. In the upper-right corner of the Q&As section, click **Import**
    
2. Click **Download Q&A template (.csv)**
    
3. Save and open the .csv file
    
4. Add the Q&A content and settings and save the file

    The .csv file should be saved as a CSV UTF-8 file, other file types and or encodings may cause import errors
    
5. In the upper-right corner of the Q&As section, click **Import**
    
6. In the Import Q&As pane, click **Browse** and navigate to the .csv file you want to import 
    
7. Click **Import**

# Prevent import errors      
You'll get an error if any required data is missing or invalid. Depending on the error, a log file may be generated with more information about the rows and columns that need to be corrected. Make any necessary edits, and try importing the file again.

> [!NOTE]
> Until all errors are resolved, you can't create or edit any Q&As. 

To help prevent errors, make sure your import file is properly formatted:
- Includes the header row that was in the import template
- Includes all columns that were in the import template
- The column order is the same as the import template
- These columns can be empty: Id, Last Modified, and Last Modified By
- The State column can't be empty, this information is required  
Based on the State field, Q&As will be saved as draft, suggested, scheduled, or they will be published automatically.

Also, if you include the Id of an existing Q&A, it will be replaced with the information in the import file.

For organizations with mulitple tenants, you can export your Q&As from one tenant and import it into another. But you must remove all of the data in the Id column before you import.

To find out more about required and recommended fields, see [Create Q&As](create-qas.md).

  

