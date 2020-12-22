---
title: "Manage Acronym answers in Microsoft Search"
ms.author: rakkum
author: rakeshMSFT
manager: jeffkizn
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Create and update Acronyms answers in Microsoft Search"
---
# Manage Acronyms answers in Microsoft Search

Users often run into unfamiliar acronyms and abbreviations used by their organization or team. Terms that are specific to organizations or teams might be new to people who move from one team to another, work with internal partner teams, or are new to the organization.

Organizations don't always have a single reference for their standard terminology. Lack of a single reference makes it hard to find definitions or expansions for these acronyms. Microsoft Search solves that problem with Acronyms.

## What users experience

Microsoft Search users can get definitions with Acronyms in [Bing](https://Bing.com), [SharePoint](https://products.office.com/sharepoint/collaboration), and [Office 365](https://Office.com). In the **Search** box, users enter queries like these examples:

- *What is* DNN
- *Define* DNN
- DNN *definition*
- *Expand* DNN
- DNN *expansion*
- *Meaning of* DNN
- DNN *means*

The result includes all the meanings of DNN that are present within the user’s organization.

> [!NOTE]
> Users must enter a query that includes the acronym’s specified *keywords* to trigger its corresponding answers. Acronym queries are not case sensitive.

## Set up acronyms answers

In the [Microsoft 365 admin center](https://admin.microsoft.com), go to [**Acronyms**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/acronyms), and then select **Add acronym**.

Microsoft Search queries two data sources to provide Acronyms answers to users’ searches:

1. **Admin-curated**. Provided by IT administrators in the [admin center](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/acronyms).
2. **System-curated**. Discovered by Microsoft Search from users' email and documents and publicly available data within the organization.

### Set up Admin-curated acronyms

Search administrators can add acronyms on the [Acronyms tab](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/acronyms) in the  [Microsoft Search admin center](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch). You can add acronyms from any internal site or repository to the admin center. These acronyms can be added to **Published** or **Draft** state:

**Published state**. Acronyms are available to the organization’s users through Microsoft Search.

> [!NOTE]
> It might take up to three days for acronyms added to Published state to become available in Microsoft Search.

**Draft state**. If admins want to review an acronyms before making it available in Microsoft Search, they can add the acronym in a Draft state. Acronyms in the Draft state will not appear in search results. You will need to move the acronym to the Published state to make it appear in search results.

You can add acronyms individually or bulk import them in a CSV file. Upload a CSV file with the fields shown in the following table:

| Acronym (mandatory) | Expansion (mandatory) | Description  | Source | State (mandatory) |
| --------- | --------- | ---------- | --------- |--------- |
| *XXX* | *Spelled out abbreviation* |  | *URL* | *Published or Draft* |

### CSV fields

**Acronym**. Contains the actual short form or acronym. An example is *DNN*.

**Expansion**. Contains the expansion of the acronym. An example is *Deep Neural Network*.

**Description**. A brief description of the acronym that gives users more info about the acronym and its expansion. For example, *A deep neural network is a neural network with a certain level of complexity, a neural network with more than two layers*.

**Source**. The URL of the page or website where you want users to go for more information about the acronym.

**State**. This field can take two values:

- **Draft**. Adds  the acronym to the Draft state.
- **Published**. Adds the acronym to the Published state and makes it available in Microsoft Search.

### System-curated acronyms

It might be a challenge for admins to add all the acronyms used within an organization to Answers. This feature can find acronyms that search administrators aren’t even aware of. To do that work, Microsoft Search also discovers and curates acronyms from these sources:

- Users’ emails
- Documents in [SharePoint](https://products.office.com/sharepoint/collaboration), [Microsoft OneDrive]( https://onedrive.live.com/about/), and [Microsoft OneNote](https://www.onenote.com/)
- Public documents within the organization that users have access to in SharePoint, OneDrive, or OneNote

Microsoft Search makes sure that only users with access and permissions to a document can see the acronyms that are discovered from it. When an acronym is found in a user's mailbox, only that user can see that acronym.

> [!NOTE]
> No setup is needed for admin-curated acronyms.

## Frequently asked questions

**Q: How is admin-curated and system-curated data ranked?**

**A:** The ranking of results may vary from person to person as results are personalized for each user. Neither of these categories will always take precendence over the other.

**Q: How long does it take for admin-curated acronyms to be visible in Microsoft Search after they’re published?**

**A:**  It takes up to three days for acronyms added to Published state to become available in Microsoft Search.

**Q: How do users trigger acronyms answers?**

**A**: To get acronyms answers, users must enter specific query patterns in a [Bing](https://bing.com), [SharePoint](https://products.office.com/sharepoint/collaboration), or [Office 365](https://Office.com) **Search** box.

**Q: How long does it take for system-curated acronyms to appear after you receive or send a new email or document?**

**A:** Acronyms found in a new email or document take up to seven days to appear in Microsoft Search results.

**Q: Do documents need to be in a specific format for mining to pick them up?**

**A:** No. We support all file types except image, folders, and zip files.

**Q: Will Microsoft discover acronyms from documents in all languages?**

**A**: Microsoft only supports mining from documents in English. Support for other languages will be added in phases.

**Q: What if my organization doesn’t want to show system-curated acronyms? Can I stop showing this type of acronym in my search results?**

**A**: To turn off showing system-curated acronyms in search results, create a customer support ticket by following the instructions at [Contact support for business products](https://docs.microsoft.com/office365/admin/contact-support-for-business-products?redirectSourcePath=%252f%252farticle%252fContact-Office-365-for-business-support-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b&view=o365-worldwide&tabs=online#BKMK_call_support).
After you create a support ticket, it takes up to 48 hours for system-curated acronyms to stop appearing in search results.
