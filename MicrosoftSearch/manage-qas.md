---
title: "Manage Q&As"
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
ms.assetid: 7e3432e6-5317-4d63-90b0-52da6fddd343
description: "Find and update answers individually or use available Microsoft Search tools to edit them all at once"
---

# Manage Q&As

Over time, you may need to update a Q&A's status and content to keep it relevant.
  
## Filter Q&As

Use the filter option in the upper-right corner of the Q&As page to find Q&As by date and who modified them. For example, set the date slider to 30 days and select an admin or editor to see the list of Q&As they've created or changed in that time.
  
## Change Q&A content or settings

1. Go to the Microsoft Search Admin portal
    
2. In the navigation pane, click **Q&As**
    
3. To find a Q&A, search, filter, or click a Q&A status to narrow your results
    
4. To change or update a Q&A, click the title
    
5. Make any changes or updates to the content or settings and preview how they'll appear
    
6. Click **Save**
    
## Bulk export and edit Q&As

Never edit data in these fields:
  
- Id
    
- Last Modified
    
- Last Modified By
    
Id is a unique identifier for each Q&A and should never be edited. The Last Modified and Last Modified By fields should only be used to sort and find Q&As.
  
1. If you want to export a subset of your Q&As, filter them
    
2. In the upper-right corner of the Q&As page, click **Export**
    
3. Save or open the .csv file
    
4. Edit data in any of these fields:
    
   - Question
    
   - URL
      
   - Keywords
    
   - State
    
   - Answer Description
    
   - Reserved Keywords
    
   - Start Date
    
   - End Date
    
   - Country/Region
    
   - Groups
    
   - Device&amp;OS
    
   - Targeted Variations
    
5. Save the .csv file
    
6. In the upper-right corner of the Q&As page, click **Import**
    
7. In the Import Q&As pane, click **Browse** and select the edited .csv file 
    
8. Click **Import**
    
You'll get an error if any required data is missing or invalid. Depending on the error, a log file may be generated with more information about the rows and columns that need to be corrected. Make any necessary edits, and try importing the file again.
  
> [!NOTE]
> Until all errors are resolved, you can't create or edit any Q&As. 
  
Not all fields are required and required fields vary depending on the Q&A state. Based on the state field, Q&As will be saved as draft, suggested, scheduled, or they will be published automatically. Find out more about required and recommended fields in [create Q&As](create-qas.md).

  

