---
title: "Manage Acronym answers in Microsoft Search"
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
description: "Create and update Acronyms answers in Microsoft Search"
---
# Manage Acronyms answers in Microsoft Search

Users often run into unfamiliar acronyms and abbreviations used by their organization or team. Terms that are specific to organizations or teams might be new to people who move from one team to another, those who work with internal partner teams, or are new to the organization.

Organizations don't always have a single reference for their standard terminology. Lack of a single reference makes it hard to find definitions or expansions for these acronyms. Microsoft Search solves that problem with Acronyms.

## What users experience
Microsoft Search users can get definitions with Acronyms in [Bing](https://Bing.com). In the **Search** box, users enter queries like these examples:

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

## Set up Acronyms answers
In the Microsoft 365 [admin center](https://admin.microsoft.com), go to **Settings** > **Microsoft Search** >**Acronyms**, and then select **Add acronyms**. 

Microsoft Search queries two data sources to provide Acronyms answers to users’ searches:

1.	**Editorial acronyms**. Provided by IT administrators in the [admin center](https://admin.microsoft.com).
2.	**Mined acronyms**. Mined by Microsoft Search from the user’s personal email and documents and publicly available data within the organization.

### Set up editorial acronyms
Search administrators can set up editorial acronyms on the [Acronyms tab](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch) in the  [Microsoft 365 admin center]( https://admin.microsoft.com). You can add acronyms from any internal site or repository to the admin center. Editorial acronyms can be added to **Published** or **Draft** state:

**Published state**. Acronyms are available to the organization’s employees through Microsoft Search.

> [!NOTE]
> It might take up to three days for acronyms added to Published state to become available in Microsoft Search.

**Draft state**. If admins want to review Acronyms answers before making them available in Microsoft Search, they can add the acronyms to Draft state. Acronyms added to Draft state aren’t available in Microsoft Search. Admins need to add the acronyms to Published state to make them available.

Admins can add acronyms individually or bulk import them in a CSV file. Upload a CSV file with the fields shown in the following table:

| Acronym (mandatory) | Expansion (mandatory) | Description  | Source | State (mandatory) |
| --------- | --------- | ---------- | --------- |--------- |
| *XXX* | *Spelled out abbreviation* |  | *URL* | *Published or Draft* |

### CSV fields
**Acronym**. Contains the actual short form or acronym. An example is *DNN*.

**Expansion**. Contains the expansion of the acronym. An example is *Deep Neural Network*.

**Description**. A brief description of the acronym that gives users quick insight into what the acronym and its expansion mean. For example, *A deep neural network is a neural network with a certain level of complexity, a neural network with more than two layers*.

**Source**. The URL of the page or website where you want users to go for more information about the acronym.

**State**. This field can take two values:

- **Draft**. Adds  the acronym to the Draft state.
- **Published**. Adds the acronym to the Published state and makes it available in Microsoft Search.

### Mined acronyms
It might be a challenge for admins to add all the acronyms used within an organization to Answers. This feature can find acronyms that search administrators aren’t even aware of. To do that work, Microsoft Search also mines acronyms from these sources:

- Users’ emails.
- Documents in [SharePoint](https://products.office.com/sharepoint/collaboration), [Microsoft OneDrive]( https://onedrive.live.com/about/) and [Microsoft OneNote](http://www.onenote.com/).
- Public documents within the organization that users have access to in SharePoint, OneDrive, or OneNote.

Microsoft Search makes sure that only users with access and permissions to a document can see the acronyms that are mined from it. When an acronym is mined from a user's mailbox, only that user can see that acronym.

> [!NOTE]
> No setup is needed for mined acronyms.

## Frequently asked questions
**Q: How is editorial and mined data ranked?**

**A:** The feature currently ranks editorial acronyms above mined acronyms.

**Q: How long does it take for editorial acronyms to be visible in Microsoft Search after they’re published?**

**A:**  It takes up to three days for acronyms added to Published state to become available in Microsoft Search. 

**Q: How do users trigger Acronyms answers?**

**A**: To get Acronyms answers, users must enter specific query patterns in a [Bing](https://bing.com) **Search** box. Currently, Acronym answers aren't available in [Office 365](https://Office.com) or [SharePoint](https://products.office.com/sharepoint/collaboration).

**Q: How long does it take for mined acronyms to appear after you receive or send a new email or document?**

**A:** Mined acronyms from a new email or document take up to seven days to appear in Microsoft Search results.

**Q: Do documents need to be in a specific format for mining to pick them up?**

**A:** No. We support all file types except image, folders, and zip files.

**Q: Will Microsoft mine acronyms from documents in all languages?**

**A**: Microsoft only supports mining from documents in English. Support for other languages will be added in phases.

**Q: What if my organization doesn’t want to show mined acronyms? Can I stop showing mined acronyms in search results?**

**A**: To turn off showing mined acronyms in search results, create a customer support ticket by following the instructions at [Contact support for business products](https://docs.microsoft.com/office365/admin/contact-support-for-business-products?redirectSourcePath=%252fen-us%252farticle%252fContact-Office-365-for-business-support-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b&view=o365-worldwide&tabs=online#BKMK_call_support).
After you create a support ticket, it takes up to 48 hours for mined acronyms to stop appearing in search results. 

**Q: When will I see Acronyms answers in [Office 365](https://Office.com) and [SharePoint Online](https://products.office.com/sharepoint/collaboration)?**

**A**: Acronyms answers in Office 365 and SharePoint Online are part of our product roadmap, but we're currently unable to provide a date or timeframe.
