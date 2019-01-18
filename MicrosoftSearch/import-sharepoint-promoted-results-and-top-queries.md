---
title: "Import SharePoint promoted results and top queries"
ms.author: dawholl
author: dawholl
manager: kellis
ms.date: 9/8/2018
ms.audience: Admin
ms.topic: reference
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
ms.assetid: 3d2a1498-174e-4214-9cf1-8b58cce5a872
description: "Use search queries from SharePoint to create work results for Microsoft Search"
---

# Import SharePoint promoted results and top queries

To leverage users' queries and Best Bets you've created in SharePoint, Microsoft Search includes two tools to import this information as suggested bookmarks: 
  
## Import SharePoint promoted result query rules

Import these rules, previously called Best Bets, as suggested bookmarks. To make them available to your users, publish them. Publishing time varies based on the number of bookmarks you select.
  
## Import top SharePoint queries using PowerShell

- Download the top queries from your SharePoint. The PowerShell script will prompt you for your SharePoint administrator credentials.
    
- Run a SharePoint search for each of the top queries to get the top search result.
    
- Add suggested bookmarks to the Admin portal.
    
- Your top SharePoint queries are excellent candidates for bookmarks. Use the PowerShell script to import them as suggested bookmarks. This script will:
    
For information about requirements, examples, and available parameters, download the script and review the README file. After the PowerShell script runs, an admin or editor should review the suggested bookmarks and make any necessary edits before they're published.

  

