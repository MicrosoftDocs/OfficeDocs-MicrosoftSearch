---
title: "MediaWiki Graph connector for Microsoft Search"
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
description: "Set up the MediaWiki Graph connector for Microsoft Search"
---

# MediaWiki Graph connector

The MediaWiki Graph connector allows your organization to discover and index data from a wiki created by using MediaWiki software. This connector indexes specified content into Microsoft Search and supports periodic crawls to keep the index up to date.

> [!NOTE]
> Read the [**Setup your Graph connector**](configure-connector.md) article to understand the general Graph connectors setup process.

This article is for anyone who configures, runs, and monitors a ServiceNow Graph connector. It supplements the general setup process, and shows instructions that apply only for the MediaWiki Graph connector. This article also includes information about [Limitations](#limitations).

<!---## Before you get started-->

<!---Insert "Before you get started" recommendations for this data source-->

## Step 1: Add a Graph connector in the Microsoft 365 admin center

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 2: Name the connection

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 3: Configure the connection settings

Enter your **Wiki URL** and choose the **Authentication type** from the drop-down menu of options. The options are **None**, **Basic**, and **OAuth
2.0 AAD**.

If you choose **Basic** as the Authentication type, you will need to provide the **Username** and **Password** for the wiki.

If you choose **OAuth 2.0 AAD** as the Authentication type, you will need to provide the **Resource ID** of the wiki installation. You will also need to provide the **Client ID** and **Client secret** generated on the AAD Application registration page.

## Step 4: Manage search permissions

The MediaWiki connector only supports search permissions visible to **Everyone**. Indexed data appears in the search results and is visible to all users in the organization.

## Step 5: Assign property labels

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 6: Manage schema

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 7: Choose refresh settings

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 8: Review connection

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

<!---## Troubleshooting-->
<!---To be added-->

## Limitations

The MediaWiki connector has these limitations in the preview release:

* Supports only cloud-based wikis.
* Supports only Basic or OAuth 2.0 with Azure Active Directory or Azure authentication.
* Doesn't support namespace selection for indexing. Indexes only Main, Category, and File namespaces.
* Doesn't support Access Control Lists (ACLs). Thus, indexed pages are visible to all users in the organization.
