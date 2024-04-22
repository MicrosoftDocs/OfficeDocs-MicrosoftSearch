---
title: "Manage Q&As"
ms.author: bstucker
author: bstuck
manager: bstucker
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
ms.assetid: 7e3432e6-5317-4d63-90b0-52da6fddd343
description: "Find and update answers individually or use available Microsoft Search tools to edit Q&As all at once."
ms.date: 01/08/2019
---

# Manage Q&As

Creating a Q&A is similar to creating bookmarks. Q&As allow you to answer the user's questions instead of just providing a link to a webpage. You can also format the answer in rich text. If a bookmark and a Q&A share the same keyword, the bookmark result appears first. Like bookmarks, the Q&A index is refreshed immediately after a Q&A is added or changed.

## Add or edit a single Q&A

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to [**Q&A**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/qnas)
1. To add a Q&A, select **Add**.
To edit a Q&A, select the Q&A in the relevant Q&A list. As you add or edit the information, the preview automatically updates.
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

## Add or edit Q&As using browser extensions

Search administrators can easily create Q&A and bookmark answers using the [Microsoft Search content creator extension](https://chrome.google.com/webstore/detail/microsoft-search-content/nocnablpaoeecfmfnjoheefkogmleipm). Add the extension to Microsoft Edge or Google Chrome, sign in with your admin account, then go to a page or site. The extension will suggest bookmark and Q&A answers based on the page content. You can publish or save them as drafts.

## Bulk add or edit Q&As

Administrators can use the Import and Export features to bulk create or edit Q&As.

Use the Import/Export feature to:

- Bulk add Q&As - Add details in the Q&A template file, and then import it.
- Bulk edit Q&As - Export Q&As to a .csv file, edit the Q&A details in the exported file, and then import the file.
- Back up Q&As - Export Q&As to a .csv file.

To import or export Q&As:

1. In the upper-right corner of the Q&A tab, select **Import**.
Select **Export** to download all the existing Q&As in a .csv file.
1. In the right pane, select the option to import by using a .csv file. Download the template file to get a list of the required fields and details.
1. Add or edit Q&A details in the template file, and save it on your computer.
1. In the **Import Q&A** pane, select **Browse**, and then select the .csv file that you want to import.
1. Select **Import**.

Important template file tips:

- Never edit data in these fields: **Id**, **Last Modified**, and **Last Modified By**
- If you include the **Id** of an existing Q&A, it will be replaced with the information in the import file.
- Not all fields in the template file are required, and the required fields vary depending on the Q&A state.
- The **State** field determines if Q&As are saved as *draft*, *suggested*, or *scheduled*, or are published automatically.
- For partners who manage multiple organizations: You can export your Q&As from one org and import them into another. But you must remove the data in the **Id** column before you import.

> [!NOTE]
> You can't import Q&As if there are any errors in the template file. To prevent errors, make sure your import file is properly formatted, and include all the required information.

For more information about avoiding errors, see [Prevent import errors](manage-bookmarks.md#prevent-import-errors).

## About keywords and reserved keywords

A Q&A can have several keywords and share the same keyword with other answers, but reserved keyword can't be shared. A reserved keyword is a unique term or phrase that triggers one specific answer. A reserved keyword can be associated with one answer only. Use reserved keywords sparingly.

## Frequently asked questions

**Q: How long does it take for a Q&A to be visible in Microsoft Search after it's published?**

**A:**  A Q&A is available in Microsoft Search immediately after publishing.

**Q: How long does it take for a deleted Q&A to be removed from Microsoft Search results?**

**A**: Deleted Q&As are immediately removed from results.

**Q: When searching, does keyword matching for Q&As work the same as for bookmarks?**

**A:**  For Q&As, the **Automatically match similar keywords** feature is based on a dictionary of alternative keywords derived from Bing search logs. The dictionary mainly supports English. For bookmark answers, this feature uses a deep learning model to determine the similarity of different search keywords and provides a more robust level of keyword matching.
