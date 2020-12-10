---
title: "File share connector"
ms.author: rusamai
author: rsamai
manager: jameslau
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
ROBOTS: NoIndex
description: "Set up the file share connector for Microsoft Search"
---

# File share connector

With the File share Graph connector, users in your organization can search on-premise Windows file shares.

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors a file share connector. It explains how to configure your connector and connector capabilities, limitations, and troubleshooting techniques.

## Install Graph connector agent

In order to index your Windows file shares, you must install and register [Graph connector agent](on-prem-agent.md) software.

## Content requirements

### File types

Content of the following formats can be indexed and searched: DOC, DOCM, DOCX, DOT, DOTX, EML, GIF, HTML, JPEG, MHT, MHTML, MSG, NWS, OBD, OBT, ODP, ODS, ODT, ONE, PDF, POT, PPS, PPT, PPTM, PPTX, TXT, XLB, XLC, XLSB, XLS, XLSX, XLT, XLXM, XML, XPS, and ZIP. Only the textual content of these formats is indexed. All multimedia content is ignored. For any file that does not belong to this format, the metadata alone is indexed.

### File size limits

The maximum supported file size is 100 MB. Files that exceed 100 MB are not indexed. The maximum post-processed size limit is 4 MB. Processing stops when a file's size reaches 4 MB. Therefore, some phrases present in the file might not work for search.

## Connect to a data source

On the **Connect to data source** page, select **File share** and provide the name, connection ID, and description. On the next page, provide the path to the file share and select your previously installed Graph connector agent. Enter the credentials for a [Microsoft Windows](https://microsoft.com/windows) user account with read access to all the files in the file share.

## Preserve last access time

When the connector attempts to crawl a file, the "last access time" field in its metadata is updated. If you depend on that field for any archiving and backup solutions and do not want to update it when the connector accesses it, you can configure this option in the **Advanced settings** page.

## Manage search permissions

You can restrict the permission to search for any file based on Share Access Control Lists or New Technology File System (NTFS) Access Control Lists. If you want to use Share Access Control Lists, select the appropriate option on the **Advanced settings** page. If you want to use NTFS Access Control Lists, select the appropriate option on the **Manage search permissions** page.

## Assign property labels

You can assign a source property to each label by choosing from a menu of options. While this step is not mandatory, having some property labels will improve the search relevance and ensure more accurate search results for end users.

## Manage schema

On the **Manage Schema** screen, you have the option to change the schema attributes (**queryable**, **searchable**, **retrievable**, and **refinable**) associated with the properties, add optional aliases, and choose the **Content** property.

## Set the refresh schedule

The recommended default refresh schedule interval is 15 minutes, but you can change it based on your preferences.

## Result layout

We recommend you to use the default result layout for file connector results. It comes ready with appropriate icons and the controls that help you navigate to the file path. You need not run any extra steps to use the default layout. If you create a new layout for the connection you created, this new layout overrides the default layout.
