---
title: "Manage bookmarks"
ms.author: jeffkizn
author: jeffkizn
manager: parulm
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
ms.assetid: c0c814d0-f7e4-444e-b18e-09beb45c9322
description: "Create and update bookmarks and ways to bulk edit bookmark results for Microsoft Search"
---
# Manage bookmarks

You can create a bookmark in just a few steps. Each bookmark includes a title, a URL, and a set of keywords that trigger it. You can also add categories to a bookmark that can be used for sorting and filtering in the admin portal. A bookmark can have several keywords and several bookmarks can share the same keyword, but reserved keyword can't be shared. When a Bookmark is created or modified, the search index is refreshed immediately, and the bookmark is available to users immediately.

If your organization has Promoted Results set up in SharePoint, you can import the Promoted Results into **Microsoft Search** and make the imported content available to your users. This is an easy way to quickly populate search results as soon as you set up **Microsoft Search** and make it more effective for your users. We recommend that you use promoted results from SharePoint as a reference to understand how to name and create relevant search results.

## Add or edit a single bookmark

1. Go to **Microsoft 365 admin center**.
1. In the navigation pane, go to **Settings** > **Microsoft Search** > **Answers** > [**Bookmarks**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/bookmarks).
1. To add a bookmark, select **Add new**.
To edit a bookmark, select the bookmark in the relevant bookmark list.
1. As you add or edit the information, the preview automatically updates.
1. Save your changes.

## Add or edit bookmark using browser extensions

Search administrators can create search content easily by using browser extensions. Install the browser extension and then go to the site you want to add as bookmark and add the site as bookmark.

Currently, browser extensions are available for Edge and Chrome.

- To download Edge extensions, go to [Microsoft Store](https://www.microsoft.com/p/microsoft-search-content-creator/9nrqdbcbwq55?activetab=pivot:overviewtab) and download the app.
- To download Chrome extensions, go to [Chrome web store](https://chrome.google.com/webstore/detail/microsoft-search-content/nocnablpaoeecfmfnjoheefkogmleipm) and download the app.

## Bulk add or edit bookmarks

Search administrator can use the Import or Export features to bulk create or edit bookmarks. This is a very useful feature when an administrator wants to add or edit a large number of bookmarks.

Use the import/export feature to:

- Bulk add bookmarks - Add details in the bookmark template file, and then import it.
- Bulk edit bookmarks - Export bookmarks to a .csv file, then edit the bookmark details in the exported .csv file, and then import the updated .csv file.
- Import promoted sites from SharePoint.
- Backup bookmarks - Export bookmarks to a .csv file.

To import or export bookmarks:

1. In the upper-right corner of **Bookmarks** tab, select **Import**.
Select **Export** to download all the existing bookmarks in a .csv file.
1. In the right pane, choose the option to import using a .csv file or from SharePoint.
Download the template file for a list of the required fields and details.
1. Add or edit bookmark details in the template file, and then save it on your computer.
1. In the **Import bookmarks** pane, select **Browse** and then the .csv file that you want to import.
1. Select **Import**.

Here are some important points to be noted regarding the template file:

- Never edit data in these fields: *Id*, *Last Modified*, and *Last Modified By*
- If you include the *Id* of an existing bookmark, it will be replaced with the information in the import file.
- If there is an existing bookmark with the same title or URL, the bookmark will be updated with information in the import file.
- Not all fields in the template file are required and required fields vary depending on the bookmark state.
- Based on the *State* field, bookmarks will be saved as draft, suggested, scheduled, or they will be published automatically.
- For partners who manage multiple organizations, you can export your bookmarks from one org and import them into another. But you must remove the data in the *Id* column before you import.

### Prevent import errors

You'll get an error if any required data is missing or invalid, and a log file is generated with more information about the rows and columns to be corrected. Make necessary edits and try importing the file again. You cannot import or save any bookmarks until all errors are resolved.

To prevent errors, make sure your import file is properly formatted and:

- Includes the header row and all the columns that were in the import template
- The column order is the same as the import template
- All columns have values, except the three that can be empty: *Id*, *Last Modified*, and *Last Modified By*
- The *State* column is not empty, as this information is required

To prevent bookmark-to-bookmark duplication errors, follow these best practices:

- Don't use duplicate URLS for different bookmarks. If a URL is already is assigned to another bookmark and you are adding it again from an import file, then you will get an error. This also applies to duplicate URLs for other types of answers.
- Use the *bookmark ID* column when updating existing bookmarks. You can update any other property of an existing bookmark, such as keyword or description, but you should make sure the *bookmark ID* is in the appropriate column of the import file. If the *bookmark ID* is present, the service won't consider it as new addition, and it won't be processed as an error.

## Power Apps

Help your users complete tasks, such as entering vacation time or reporting expenses, by adding existing PowerApps to your bookmarks.

### Power Apps Explained

Power Apps is a service that lets you build business apps that run in a browser or on a phone or tablet with no coding experience required. PowerApps work in any browser and on any device and take less than a minute to add. For more on PowerApps, see:

- [Guided Learning](https://docs.microsoft.com/learn/browse/?products=powerapps)
- [Documentation](https://docs.microsoft.com/powerapps/maker/canvas-apps/get-sessionid)
- [Power Apps Home](https://make.preview.powerapps.com/environments/839eace6-59ab-4243-97ec-a5b8fcc104e4/home)

### Add a Power App to a bookmark

1. Find the [App ID for the Power App](https://docs.microsoft.com/powerapps/maker/canvas-apps/get-sessionid#get-an-app-id) that you want to add.
1. Sign in to the [**Microsoft 365 admin center**](https://admin.microsoft.com).
1. In the navigation pane, go to **Settings** > **Microsoft Search** > **Answers** > [**Bookmarks**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/bookmarks).
1. Add a bookmark or find an existing bookmark that you want to add a **PowerApp** to.
1. In **Bookmark settings**, select **Power App**, and then **Add a Power App**.
1. Enter or paste the **App ID**.
    The height and width are automatically adjusted. Bookmarks can support both portrait and landscape orientations, but currently the size can't be changed. The bookmark preview shows a fully functional PowerApp to make it easy to test.
1. Select **Publish** or **Save to Draft**.
