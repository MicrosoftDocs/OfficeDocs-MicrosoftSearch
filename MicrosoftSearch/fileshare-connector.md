---
ms.date: 11/12/2020
title: "File share Microsoft Graph connector"
ms.author: danielabo
author: danielabom
manager: SteveWilkins1123
audience: Admin
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
ROBOTS: NoIndex
description: "Set up the File Share Microsoft Graph connector for Microsoft Search and Microsoft 365 Copilot"
---
# File Share Microsoft Graph connector

The File Share Microsoft Graph connector allows users in your organization to search on-premises Windows file shares.

## Before you get started

### Install the Microsoft Graph connector agent

To index your Windows file shares, you must install and register the connector agent. See [Install the Microsoft Graph connector agent](graph-connector-agent.md) to learn more.  

### Content requirements

### File types

Content of the following formats can be indexed and searched: DOC, DOCM, DOCX, DOT, DOTX, EML, GIF, HTML, JPEG, JPG, MHT, MHTML, MSG, NWS, OBD, OBT, ODP, ODS, ODT, ONE, PDF, PNG, POT, PPS, PPT, PPTM, PPTX, TXT, XLB, XLC, XLSB, XLS, XLSX, XLT, XLXM, XML, XPS, and ZIP. Only the textual content of these formats is indexed and all multimedia content is ignored. The files that do not belong to these formats are skipped from getting crawled and indexed.

### File size limits

The maximum supported file size is 100 MB. Files that exceed 100 MB aren't indexed. The maximum post-processed size limit is 4 MB. Processing stops when a file's size reaches 4 MB. Therefore, some phrases present in the file might not work for search.

## Step 1: Add a connector in the Microsoft 365 admin center

[Add File Share Microsoft Graph connector](https://admin.microsoft.com/adminportal/home#/MicrosoftSearch/Connectors/add?ms_search_referrer=MicrosoftSearchDocs_FileShare&type=FileConnector)

(See general [setup instructions](./configure-connector.md) for more details)
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 2: Name the connection

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 3: Configure the connection settings

> [!NOTE]
> You can index up to twenty different file shares in a single connection. Enter one file share per line in the file shares text box area.

Enter the path to the file share and select your previously installed Microsoft Graph connector agent. Enter the credentials for a [Microsoft Windows](https://microsoft.com/windows) user account with read access to all the files in the file share.

## Step 4: Preserve last access time

When the connector attempts to crawl a file, the "last access time" field in its metadata is updated. If you depend on that field for archiving and backup solutions and you don't want to update it when the connector accesses it, select this option.

## Step 5: Limits for file indexing

You have the ability to limit files and folders from indexing based on file type, modified date, and location.

### Based on file types

For these file formats, only the text is indexed: DOC, DOCM, DOCX, DOT, DOTX, EML, HTML, MHT, MHTML, MSG, NWS, OBD, OBT, ODP, ODS, ODT, ONE, PDF, POT, PPS, PPT, PPTM, PPTX, TXT, XLB, XLC, XLSB, XLS, XLSX, XLT, XLXM, XML, XPS. For multimedia and other file types, only metadata is indexed.

### Based on the last modified date or number of days since the last modification

Use these selections to only index files modified within a specified number of days or since a specific date.

### Full network path or regular expression

In the network path, use the escape character (\\) before special characters like \\. Example: For the path \\\\CONTOSO\\FILE\\SHAREDFOLDER, correct way to input is  \\\\\\\\CONTOSO\\\\FILE\\\\SHAREDFOLDER

For information about writing regular expressions, see [Regular Expression Language Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).

You also have the ability to create an exception to the limit rule. The priority of the exception rule will supersede limit rules. Exception rules can be defined by entering folder or file paths for the items you want to include in indexing.

:::image type="content" source="media/file-connector/ExclusionRule.png" alt-text="Graphic showing a subset of files excluded from indexing with exceptions.":::

## Step 6: Custom property settings

You can enrich your indexed data by creating custom properties based on the connector's default properties.

:::image type="content" source="media/file-connector/connectors-custom-property-setup.png" alt-text="Custom property set up with a rule for URL.":::

To add a custom property:

  1. Enter a property name. This name appears in the search results from this connector.
  1. For the value, select **Static or String/Regex Mapping**. A static value is included in all search results from this connector. The string/regex value varies based on the rules you add.
  1. Select **Edit value**.
  1. If you selected a static value, enter the string you want to appear.
  1. If you selected a string/regex value:
      * In the **Add expressions** section, in the **Property** list, select a default property from the list.
      * For **Sample value**, enter a string to represent the type of values that could appear. This sample is used when you preview your rule.
      * For **Expression**, enter a regex expression to define the portion of the property value that should appear in search results. You can add up to three expressions. To learn more about regex expressions, see [Regular expression language quick reference](/dotnet/standard/base-types/regular-expression-language-quick-reference) or search the web for a regex expression reference guide.
      * In the **Create formula** section, enter a formula to combine the values extracted from the expressions. 

## Step 7: Assign property labels

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 8: Manage schema

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 9: Manage search permissions

You can restrict the permission to search for any file based on Share Access Control Lists or New Technology File System (NTFS) Access Control Lists, by selecting the desired option on the **Manage search permissions** page. The user accounts and groups provided in the Access Control Lists must be managed by Active Directory (AD). If you're using any other system for user accounts management, you can select the 'everyone' option, which lets users search for all the files without any access restrictions. However, when users try to open the file, access controls set at the source apply.

Windows by default provides 'Read' permission to 'Everyone' in Share ACLs when a folder is shared on the network. By extension, if you're choosing Share ACLs in **Manage search permissions**, users can search for all the files. If you want to restrict access, remove 'Read' access for 'Everyone' in file shares and provide access only to the desired users and groups. The connector then reads these access restrictions and applies them to the search.

You can choose to share ACLs only if the share path you provided follows UNC path format. You can create a path in UNC format by going to 'Advanced Sharing' under the 'Sharing' option.

:::image type="content" source="media/file-connector/file-advanced-sharing.png" alt-text="Screenshot of the Advanced settings dialog box.":::

## Step 10: Choose refresh settings

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 11: Review connection

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup 
instructions.-->

<!---## Troubleshooting-->
<!---Insert troubleshooting recommendations for this data source-->
## Troubleshooting
After publishing your connection, you can review the status under the **Data sources** tab in the [admin center](https://admin.microsoft.com). To learn how to make updates and deletions, see [Manage your connector](manage-connector.md).

You can find troubleshooting steps for commonly seen issues [here](troubleshoot-file-share-connector.md).

If you have any other issues or want to provide feedback, reach out to us at [Microsoft Graph | Support](https://developer.microsoft.com/en-us/graph/support).

<!---## Limitations-->
<!---Insert limitations for this data source-->

