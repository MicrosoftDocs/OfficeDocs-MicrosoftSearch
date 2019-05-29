---
title: "Manage Q&As"
ms.author: dawholl
author: dawholl
manager: kellis
ms.date: 05/30/2019
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
ms.assetid: 7e3432e6-5317-4d63-90b0-52da6fddd343
ROBOTS: NOINDEX
description: "Find and update answers individually or use available Microsoft Search tools to edit them all at once"
---

# Manage Q&As

Creating a Q&A is similar to creating bookmarks. Q&A allows you to answer the user's question instead of just providing a link to webpage. You can format the answer in rich text using the available tools. If a Bookmark and a Q&A share the same keyword, the Bookmark result is shown first. Like Bookmarks, the Q&A index is refreshed immediately after a Q&A is added or changed. 

## Add or edit a single Q&A
1. Go to **Microsoft 365 admin center**.
1. In the navigation pane, go to **Settings** and select **Microsoft Search**.
1. Select **Q&A** tab. By default, the first tab (**Bookmarks**) is selected.
1. To add a Q&A, select **Add new**.
To edit a Q&A, select the Q&A in the relevant Q&A list.
1. As you add or edit the information, the preview automatically updates.
1. Save your changes.

### Supported HTML tags
You can use existing HTML content or add HTML tags to your answer (description). Unsupported tags are ignored.  
The following HTML tags are supported:
- blockquote
- div
- em
- h1, h2, h3, and h4
- ol, ul, and li
- p
- pre
- span
- strong
- table, thead, tbody, tr, th, and td
- u
- a
- code
- br
- hr
- img

## Bulk add or edit Q&A
Administrators can use the Import and Export features to bulk create or edit Q&A. This is a useful feature when administrators need to add or edit a large number of Q&A. 

Use the import/export feature to:
1. Bulk add Q&A - Add details in the Q&A template file, and then import it.
1. Bulk edit Q&A - Export Q&A to a .csv file, then edit the Q&A details in the exported .csv file, and then import the .csv file.
1. Backup Q&A - Export Q&A to a .csv file.

To import or export Q&A:
1. In the upper-right corner of the Q&A tab, select **Import**. 
Select **Export** to download all the existing Q&A in a .csv file.
1. In the right pane, choose the option to import using a .csv file.
Download the template file for a list of the required fields and details. 
1. Add or edit Q&A details in the template file and save it on your computer. 
1. In the **Import Q&A** pane, select **Browse**, and then the .csv file that you want to import.
1. Select **Import**.

Here are some important points regarding the template file:
- Never edit data in these fields: *Id*, *Last Modified*, and *Last Modified By*
- If you include the *Id* of an existing bookmark, it will be replaced with the information in the import file.
- If there is an existing bookmark with the same title or URL, the bookmark will be updated with information in the import file.
- Not all fields in the template file are required and required fields vary depending on the bookmark state.
- Based on the State field, bookmarks will be saved as draft, suggested, scheduled, or they will be published automatically.
- For organizations with multiple tenants, you can export your bookmarks from one tenant and import it into another. But you must remove the data in the *Id* column before you import.

**Note:** You cannot import Q&A if there are any errors in the template file. To prevent errors, make sure your import file is properly formatted and include all the required information. 

For more information on how to prevent error, see [Prevent import errors](#prevent-import-errors).