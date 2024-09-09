---
ms.date: 10/08/2019
title: "MediaWiki Microsoft Graph connector"
ms.author: mecampos
author: mecampos
manager: umas
audience: Admin
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
description: "Set up the MediaWiki Microsoft Graph connector for Microsoft Search"
---
<!---Previous ms.author: monaray --->

# MediaWiki Microsoft Graph connector

The MediaWiki Microsoft Graph connector allows your organization to discover and index data from a wiki created by using MediaWiki software. This connector indexes specified content into Microsoft Search and supports periodic crawls to keep the index up to date.

> [!NOTE]
> Read the [**Set up Microsoft Graph connectors in the Microsoft 365 admin center**](configure-connector.md) article to understand the general Microsoft Graph connectors setup instructions.

This article is for anyone who configures, runs, and monitors a MediaWiki connector. It supplements the general setup process, and shows instructions that apply only for the MediaWiki connector. This article also includes information about [Limitations](#limitations).

<!---## Before you get started-->

<!---Insert "Before you get started" recommendations for this data source-->

## Step 1: Add a connector in the Microsoft 365 admin center

[Add MediaWiki connector](https://admin.microsoft.com/adminportal/home#/MicrosoftSearch/Connectors/add?ms_search_referrer=MicrosoftSearchDocs_MediaWiki&type=MediaWiki)

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 2: Name the connection

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 3: Configure the connection settings

Enter your **Wiki URL** and choose the **Authentication type** from the drop-down menu of options. The options are **None**, **Basic**, and **OAuth
2.0 Microsoft Entra ID**.

If you choose **Basic** as the Authentication type, you will need to provide the **Username** and **Password** for the wiki.

If you choose **OAuth 2.0 Microsoft Entra ID** as the Authentication type, you will need to provide the **Resource ID** of the wiki installation. You will also need to provide the **Client ID** and **Client secret** generated on the Microsoft Entra Application registration page.

## Step 4: Manage search permissions

The MediaWiki connector only supports search permissions visible to **Everyone**. Indexed data appears in the search results and is visible to all users in the organization.

## Step 5: Assign property labels

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 6: Manage schema

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 7: Choose refresh settings

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 8: Review connection

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

<!---## Troubleshooting-->
<!---To be added-->

## Limitations

The MediaWiki connector has these limitations in the preview release:

* Supports only cloud-based wikis.
* Supports only Basic or OAuth 2.0 with Microsoft Entra ID or Azure authentication.
* Doesn't support namespace selection for indexing. Indexes only Main, Category, and File namespaces.
* Doesn't support Access Control Lists (ACLs). Thus, indexed pages are visible to all users in the organization.

## Troubleshooting
After publishing your connection, you can review the status under the **Data Sources** tab in the [admin center](https://admin.microsoft.com). To learn how to make updates and deletions, see [Manage your connector](manage-connector.md).

If you have any other issues or want to provide feedback, write to us [aka.ms/TalkToGraphConnectors](https://aka.ms/TalkToGraphConnectors).
