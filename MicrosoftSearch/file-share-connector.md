---
title: "File share connector for Microsoft Search"
ms.author: v-pamcn
author: TrishaMc1
manager: mnirkhe
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Set up the file share connector for Microsoft Search."
---

# File share connector

With the File share connector, users in your organization can search on-premises file shares. The search results from these shares merge with the results from SharePoint and Microsoft OneDrive for Business.

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors a File share connector. It explains how to configure your connector and connector capabilities, limitations, and troubleshooting techniques.

## Install a data gateway
In order to access your third-party data, you must install and configure a Microsoft Power BI gateway. See [Install an on-premises gateway](https://docs.microsoft.com/data-integration/gateway/service-gateway-install) to learn more.  

## Content requirements
**File types**. Only files in these formats can be indexed and searched: DOC, DOCM, DOCX, DOT, DOTX, EML, GIF, HTML, JPEG, MHT, MHTML, MSG, NWS, OBD, OBT, ODP, ODS, ODT, ONE, PDF, POT, PPS, PPT, PPTM, PPTX, TXT, XLB, XLC, XLSB, XLS, XLSX, XLT, XLXM, XML, XPS, and ZIP. Only the textual content of these formats is indexed. All multimedia content is ignored.
 
**File size limits**. The maximum supported file size is 100 MB. Files that exceed 100 MB are skipped from indexing. The maximum post-processed size limit is 4 MB. Processing stops when a file's size reaches 4 MB. As a result, some phrases present in the file might not work for search.

## Connect to a data source
On the **Connect to data source** page, select **File share** and provide the name, connection ID, and description. In the next page, provide the path to the file share and select your previously installed gateway. Enter the credentials for a Windows user account with read access to all the files in the share. Go through the rest of the settings and publish the connection.

## Set the refresh schedule
The recommended default refresh schedule interval is 15 minutes, but you can change it to another interval that you prefer.

## Set up your search results page
To display different file connection results in the **All** and **Files** tabs, you need to set up a SharePoint search engine results page:
- The **All** table shows combined results from your file connections, SharePoint files, OneDrive files, and SharePoint sites. 
- The **Files** vertical shows all file results from your connections, SharePoint, and OneDrive.
Results from file connections are added to already existing results in both the **All** and **Files** verticals.

To set up your search results page, take these steps:
1. Create a SharePoint site collection with a modern search page.

2. Install a [SharePoint Online Management Shell](https://www.microsoft.com/download/details.aspx?id=35588).

3. Open SharePoint Online Management Shell as an administrator and import the **Microsoft.SharePoint.Client.dll** module present at `C:\Windows\Microsoft.NET\assembly\GAC_MSIL\Microsoft.SharePoint.Client\v4.0_16.0.0.0__71e9bce111e9429c\Microsoft.SharePoint.Client.dll`.

> [!NOTE]
> This path might not be the same for all users.

To import the module, run this command in SharePoint Online Management Shell:
```bash
Import-Module "C:\Windows\Microsoft.NET\assembly\GAC_MSIL\Microsoft.SharePoint.Client\v4.0_16.0.0.0__71e9bce111e9429c\Microsoft.SharePoint.Client.dll" 
```

4. Now run this script:
```bash
$orgName = Read-Host -prompt 'Please enter your org name'
$userName = Read-Host -prompt 'Enter user name'
$userCreds = Get-Credential -UserName $userName -Message "Type the password"
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $userCreds

$url = Read-Host -Prompt 'Please enter the site url'
$site = Get-SPOSite -Identity $url
Set-SPOSite $url -DenyAddAndCustomizePages 0

$pwd = Read-Host -AsSecureString 'type the password'
$context = New-Object Microsoft.SharePoint.Client.ClientContext($url)
$credential = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($userName, $pwd)
$context.Credentials = $credential
$web = $context.Web
$context.Load($web)
$web.AllProperties["AllVerticalContent"] = "Combined"
$web.Update()
$context.ExecuteQuery()
$web.AllProperties["FilesVerticalContent"] = "ConnectorsOnly"
$web.Update()
$context.ExecuteQuery()
Set-SPOSite $url -DenyAddAndCustomizePages 1

Write-Host "Success" -ForegroundColor Cyan
Read-Host -Prompt 'Press enter to exit'
```

5. Enter the required values in PowerShell, such as organization name, username, password, and site URL. As an **example**, if your admin credentials are `admin@a830edad9050849823J19081300.onmicrosoft.com`, then your organization name is **a830edad9050849823J19081300**, and your site URL is `https:// a830edad9050849823J19081300.sharepoint.com`.

> [!NOTE]
> The **AllProperties** setting can only be done at a site collection level (Teams/Comms site).

6. Now you can search for indexed files and see results in both the **All** and **Files** tabs.

## Search for file share content in the search results page
To search for indexed content, go to the SharePoint home page of your test tenant. Results will be displayed in the **All** and **Files** tabs.

Because of browser restrictions, you can't select a file result to view or open files from local file share searches. To open these files, copy the file result's link and paste it into the address bar of your system's browser. For Windows, use Windows Explorer. Then you can open the file on your system.

![SharePoint search with the copy link dialog box open.](media/fileshare-search.png)

## Troubleshooting
If something is critically wrong with a connection, its status shows as **failed**. To get more information on the three types of errors, go to the **error details** page and select the failing connection. See [Manage your connector](manage-connector.md) to learn more.
1. **Gateway not reachable (error code: 11)**. The gateway machine for the connection is down. Verify if the Microsoft Power BI process runs on the gateway machine.
2. **Authentication error (error code: 12)**. The credentials that were used for creating the connection expired or are no longer valid. To resolve this error, enter valid credentials.
3. **Internal error (error code: anything other than 11 or 12)**. There's an error in the connector infrastructure. See the [Feedback](connectors-feedback.md) article to find out how to report these errors.

## Limitations
The File share connector has these limitations in the preview release:
* You can only index files with fixed properties, not files with custom properties.
* File share Access Control Lists (ACLs) aren't currently supported. Only file NTFS ACLs are supported.
* External identities aren't supported. They must be mapped to Azure Active Directory identities.
