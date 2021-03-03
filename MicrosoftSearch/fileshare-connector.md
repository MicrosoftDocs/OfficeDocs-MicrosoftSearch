---
title: "File share Graph connector for Microsoft Search"
ms.author: mecampos
author: mecampos
manager: umas
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
ROBOTS: NoIndex
description: "Set up the File share Graph connector for Microsoft Search"
---
<!---Previous ms.author: rusamai --->

# File share Graph connector

The File share Graph connector allows users in your organization to search on-premise Windows file shares.

> [!NOTE]
> Read the [**Setup for your Graph connector**](configure-connector.md) article to understand the general Graph connectors setup process.

## Before you get started

### Install the Graph connector agent

To index your Windows file shares, you must install and register the Graph connector agent. See [Install the Graph connector agent](on-prem-agent.md) to learn more.  

### Content requirements

### File types

Content of the following formats can be indexed and searched: DOC, DOCM, DOCX, DOT, DOTX, EML, GIF, HTML, JPEG, MHT, MHTML, MSG, NWS, OBD, OBT, ODP, ODS, ODT, ONE, PDF, POT, PPS, PPT, PPTM, PPTX, TXT, XLB, XLC, XLSB, XLS, XLSX, XLT, XLXM, XML, XPS, and ZIP. Only the textual content of these formats is indexed. All multimedia content is ignored. For any file that doesn't belong to this format, the metadata alone is indexed.

### File size limits

The maximum supported file size is 100 MB. Files that exceed 100 MB aren't indexed. The maximum post-processed size limit is 4 MB. Processing stops when a file's size reaches 4 MB. Therefore, some phrases present in the file might not work for search.

## Step 1: Add a Graph connector in the Microsoft 365 admin center

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 2: Name the connection

Follow the general [setup instructions](https://docs.microsoft.com/microsoftsearch/configure-connector).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 3: Configure the connection settings

On the **Connect to data source** page, select **File share** and provide the name, connection ID, and description. On the next page, provide the path to the file share and select your previously installed Graph connector agent. Enter the credentials for a [Microsoft Windows](https://microsoft.com/windows) user account with read access to all the files in the file share.

### Preserve last access time

When the connector attempts to crawl a file, the "last access time" field in its metadata is updated. If you depend on that field for any archiving and backup solutions and doesn't want to update it when the connector accesses it, you can configure this option in the **Advanced settings** page.

## Step 4: Manage search permissions

You can restrict the permission to search for any file based on Share Access Control Lists or New Technology File System (NTFS) Access Control Lists, by selecting the desired option in **Manage search permissions** page. The user accounts and groups provided in these Access Control Lists must be managed by Active Directory (AD). If you are using any other system for user accounts management, you can select 'everyone' option, which lets users search for all the files without any access restrictions. However, when users try to open the file, access controls set at the source apply.

Note that windows by default provides 'Read' permission to 'Everyone' in Share ACLs when a folder is shared on network. By extension, if you are choosing Share ACLs in **Manage search permissions**, users will be able to search for all the files. If you want to restrict access, remove 'Read' access for 'Everyone' in file shares and provide access only to the desired users and groups. The connector then reads these access restrictions and applies them to search.

You will not be able choose Share ACLs if the share path you provide does not follow the pattern \\<server-name>\<share-name>. If your share path has the format \\<server-name>\<folder1>\<share-name>, you can create a path in the supported format by going to 'Advanced Sharing' under 'Sharing' option for a file share.

![Advanced_sharing](media/file-connector/file-advanced-sharing.png)

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
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup 
instructions.-->

<!---## Troubleshooting-->
<!---Insert troubleshooting recommendations for this data source-->

<!---## Limitations-->
<!---Insert limitations for this data source-->
