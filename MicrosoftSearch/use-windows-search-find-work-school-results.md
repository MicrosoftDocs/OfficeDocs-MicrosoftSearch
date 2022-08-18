---
title: "Use Windows Search to find work or school results"
ms.author: dawholl
author: dawholl
manager: kellis
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
ms.assetid: f980b90f-95e2-4b66-8b21-69f601ff4b50
ROBOTS: NoIndex
description: "Use Windows Search to find work or school files, sites, people, and more right from your desktop."
---

# Use Windows Search to find work or school results

Windows Search is a desktop search experience that helps users find relevant results. When users search from the taskbar they'll get results from:

- **Your organization**: When signed in to Windows Search with a work or school account, users will see suggestions and results from SharePoint, OneDrive for Business, Microsoft Graph, and other data sources connected to Microsoft Search.
- **The web**: Users will get relevant search suggestions and results from Bing.
- **The device**: Users can find local files, settings, and apps on their PC.
  
## Microsoft Search in Windows

Windows Search brings Microsoft Search results to every PC. Just start typing in the integrated Windows Search box to find relevant answers and results from your organization, including people, bookmarks, locations, Q&As, files, and more.

## Prepare for Microsoft Search in Windows

To provide work or school results in Windows Search, a few requirements must be met:

- Using Windows 10 version 1809, Build 17763, RS5 October 2018 Update or later
- Microsoft Search in Bing is turned on for your organization
- Web search in Windows is enabled
- Cloud Content enabled for work or school account
- Windows Search connected to work or school account (Azure AD)

### Turn on Microsoft Search in Bing

For most organizations, including enterprise and education, Microsoft Search in Bing is on by default. To turn on Microsoft Search in Bing, go to the [Configurations](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/configurations) page in the Microsoft 365 admin center. Under Microsoft Search in Bing setting, choose **Change** and select **Enable Microsoft Search in Bing at your organization**. It takes up to 24 hours for this change to take effect.

If this setting is off, users won't get internal results when they search on Windows Search, in Microsoft Edge, or on Bing. Turning off Microsoft Search in Bing doesn't stop or prevent internal content from being added to your search index. It only disables these entry points to Microsoft Search.

:::image type="content" alt-text="Screenshot of of Microsoft Search people answer in Windows Search." source="media/windows-search/admin-center-microsoft-search-bing-setting.png":::

### Enable web search in Windows

If web search is enabled on your local device, you should see the Web tab in the Windows Search box.

:::image type="content" alt-text="Screenshot of of Microsoft Search people answer in Windows Search." source="media/windows-search/windows-search-web-tab.png":::

If web search is disabled in Windows, your users won't see search suggestions or results from your organization. To allow work or school suggestions and results, enable web search using group policy and a registry key:

- Group policy path and setting: ```Computer Configuration/Administrative Templates/Windows Components/Search/Don’t search the web or display web results in Search``` This policy should be set to Disabled. Learn more about [DoNotUseWebResults MDM policy CSP](/windows/client-management/mdm/policy-csp-search#search-donotusewebresults).
- Registry key path and setting: ```HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Search\BingSearchEnabled``` This registry key value should be 1.

### Enable cloud content

If you turn on the Work or School account setting for Cloud content search, Windows Search will show results from OneDrive for Business, Outlook, SharePoint, and more from Microsoft Search.

:::image type="content" alt-text="Screenshot of of Microsoft Search people answer in Windows Search." source="media/windows-search/windows-setting-cloud-content-search.png":::

You can use group policy and registry keys to validate if Cloud content search permissions are enabled in your local device:

- Group policy path and setting: ```Computer Configuration/Administrative Templates/Windows Components/Search/Allow Cloud Search``` This policy should be set to Enabled. Learn more about [Allow Cloud Search MDM policy CSP](/windows/client-management/mdm/policy-csp-search#search-allowcloudsearch).
- Registry key paths and settings: ```HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\SearchSettings\IsAADCloudSearchEnabled``` and ```HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Windows SearchAllowCloudSearch``` Both registry key values should be 1.

### Connect work or school account (Azure AD) to Windows Search

To verify a user's identity and determine the information and files they can access, Microsoft Search uses their work or school account. Your users can follow these steps to connect Windows Search with their work or school account:

1. Open the **Settings** app.
2. Select **Accounts**.
3. Select **Access work or school**.
4. Check for your account. If it's not listed, select the **Connect** button to add it.
5. Sign in with your work or school credentials.
6. Follow the onscreen prompts to finish connecting.  
7. When complete, your account will be added as a connection. You'll have access to search suggestions, results, and other resources your organization makes available.  

## Search highlights in Windows

Search Highlights in [Windows 10](https://blogs.windows.com/windows-insider/2022/03/14/releasing-windows-10-build-19044-1618-to-release-preview-channel/) and [Windows 11 (Insider Preview)](https://blogs.windows.com/windows-insider/2022/03/09/announcing-windows-11-insider-preview-build-22572/) feature the latest updates from your organization and suggested people, files, and more. Users can explore files or browse through your organization’s people chart. As always, users can just start typing to find everything related to your organization, right at their fingertips using Search.

:::image type="content" alt-text="Screenshot of of Microsoft Search people answer in Windows Search." source="media/windows-search/search-highlights-organization.png":::

### Manage Search Highlights

Users have the ability to show or hide Search Highlights. To turn it off or back on, right-click the taskbar, select **Search**, and then select or clear **Show search highlights**.

Windows and Microsoft 365 IT admins can also control how Search Highlights on the taskbar are configured for Windows 10 and Windows 11 managed devices. Learn more about [Allow Search Highlights MDM policy CSP](/windows/client-management/mdm/policy-csp-search#search-allowsearchhighlights). 

To manage Search Highlights with group policy go to the policy setting ```Computer Configuration/Administrative Templates/Windows Components/Search/Allow search highlights```. Use the setting to disable or enable the search highlights experience. If you leave the setting as **Not Configured** the experience is enabled by default.
The supported settings values in Windows 10:

- Enabled (default) or Not Configured: Enabling or not configuring this setting turns on search highlights in the taskbar search box and in Windows Search home.
- Disabled:Disabling this setting turns off search highlights in the taskbar search box and in Windows Search home.

The supported values in Windows 11:

- Enabled (default) or Not Configured: Enabling or not configuring this setting turns on search highlights in the Start menu search box and in Windows Search home.
- Disabled: Disabling this setting turns off search highlights in the Start menu search box and in Windows Search home.

To access the policy for search highlights, on a device with the March 2022 Cumulative Update Preview or April 2022 monthly quality update, go to **C:\Windows\PolicyDefinitions** and locate **Search.admx**. If needed, the Microsoft Download Center has an updated version of the [Administrative Templates](https://www.microsoft.com/download/details.aspx?id=104042) (.admx) and [Group Policy Settings Reference](https://www.microsoft.com/download/details.aspx?id=104043) for Windows 10, version 20H2. Microsoft Endpoint Manager offers the same policy configuration options.
