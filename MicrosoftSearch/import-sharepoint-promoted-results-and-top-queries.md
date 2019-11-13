---
title: "Import SharePoint promoted results and top queries"
ms.author: dawholl
author: dawholl
manager: kellis
ms.audience: Admin
ms.topic: reference
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
ms.assetid: 3d2a1498-174e-4214-9cf1-8b58cce5a872
ROBOTS: NOINDEX
description: "Use search queries from SharePoint to create work results for Microsoft Search"
---

# Import SharePoint promoted results and top queries

> [!IMPORTANT]
> This article applies to the Microsoft Search in Bing admin portal. We’re moving the portal to the Microsoft 365 admin center, and then the Microsoft Search in Bing portal will be removed. We recommend that you use the Microsoft 365 admin center to get started. [Overview of Microsoft Search](overview-microsoft-search.md).
    
To leverage users' queries and Best Bets you've created in SharePoint, Microsoft Search includes two tools to import this information as suggested bookmarks: 
  
## Import SharePoint promoted result query rules

Import these rules, previously called Best Bets, as suggested bookmarks. To make them available to your users, publish them. Publishing time varies based on the number of bookmarks you select.
  
## Import top SharePoint queries using PowerShell

- Download the top queries from your SharePoint. The PowerShell script will prompt you for your SharePoint administrator credentials.
    
- Run a SharePoint search for each of the top queries to get the top search result.
    
- Add suggested bookmarks to the Admin portal.
    
- Your top SharePoint queries are excellent candidates for bookmarks. Use the PowerShell script to import them as suggested bookmarks. This script does the following work:
    - Adds suggested bookmarks based on SharePoint top queries to improve Microsoft Search bookmark coverage. This script downloads the top queries accessible from SharePoint admin portal, and then uploads them as suggested bookmarks for an admin to review in the Microsoft Search admin portal.
    - By default, the script adds suggested bookmarks to given tenant for all available months. It gets top queries from a given SharePoint admin website and adds them to Microsoft Search as suggested bookmarks. Suggested bookmarks need an admin/editor to approve them in the admin portal before being published. When you run this script, you are prompted for credentials to access the Microsoft Search admin portal.
    - The script allows additional parameters to be specified. You can, for example, add suggested bookmarks to given tenant for top N queries in each of the available months.
    - Optionally, you can add suggested bookmarks to given tenant for months in the given year. This command gets top queries for the given time period from SharePoint admin website and adds them to Microsoft Search as suggested bookmarks.
    - As well, there are numerous other options and command modes: download top queries from SharePoint to a specified folder, run the script in Safe mode, run the script in Verbose mode, and a Debug mode.
    - Download the script [here](https://www.bingforbusiness.com/distribution/SharepointTopQueryBookmarks.zip). 

For information about requirements, examples, and available parameters, download the script and review the README file. After the PowerShell script runs, an admin or editor should review the suggested bookmarks and make any necessary edits before they're published.