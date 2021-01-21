---
title: "MediaWiki connector for Microsoft Search"
ms.author: monaray
author: monaray97
manager: mnirkhe
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Set up the MediaWiki connector for Microsoft Search"
---

# MediaWiki connector

With the MediaWiki connector, your organization can discover and index data from a wiki created by using MediaWiki software. This 
connector indexes specified content into Microsoft Search and supports periodic crawls to keep the index up to date.

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors a MediaWiki Graph connector. It supplements the
general instructions provided in the [Set up your Graph connector](configure-connector.md) article. If you have not 
already done so, read the entire Set up your Graph connector article to understand the general setup process.

Each step in the setup process is listed below along with either a note that indicates you should follow the general setup instructions OR 
other instructions that apply to only MediaWiki Graph connectors. This article also includes information about [Limitations](#limitations) for MediaWiki Graph connectors. 

## Step 1: Add a Graph connector in the Microsoft 365 admin center.
Follow the general setup instructions.

## Step 2: Name the connection.
Follow the general setup instructions.
 
## Step 3: Configure the connection settings.
Enter your **Wiki URL** and choose the **Authentication type** from the drop-down menu of options. The options are **None**, **Basic**, and **OAuth
2.0 AAD**.

If you choose **Basic** as the Authentication type, you will need to provide the **Username** and **Password** for the wiki.

If you choose **OAuth 2.0 AAD** as the Authentication type, you will need to provide the **Resource ID** of the wiki installation. You will also 
need to provide the **Client ID** and **Client secret** generated on the AAD Application registration page. 

## Step 4: Manage search permissions
The MediaWiki connector only supports search permissions visible to **Everyone**. Indexed data appears in the search results and is visible to all 
users in the organization.

## Step 5: Assign property labels
Follow the general setup instructions.

## Step 6: Manage schema
Follow the general setup instructions.

## Step 7: Choose refresh settings
Follow the general setup instructions.

## Step 8: Review connection
Follow the general setup instructions.

<!---## Troubleshooting-->
<!---To be added-->

## Limitations
The MediaWiki connector has these limitations in the preview release:

* Supports only cloud-based wikis.
* Supports only Basic or OAuth 2.0 with Azure Active Directory or Azure authentication.
* Doesn't support namespace selection for indexing. Indexes only Main, Category, and File namespaces.
* Doesn't support Access Control Lists (ACLs). Thus, indexed pages are visible to all users in the organization.
