---
title: "Manage Acronym answers in Microsoft Search"
ms.author: rakkum
author: rakeshMSFT
manager: bstucker
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
description: "Create and update Acronyms answers in Microsoft Search"
ms.date: 10/02/2019
---

# Manage Acronyms answers in Microsoft Search

Users often run into unfamiliar acronyms and abbreviations used by their organization or team. Terms specific to organizations or teams might be new to people who move from one team to another, work with internal partner teams, or are new to the organization.

Organizations don't always have a single reference for their standard terminology. Lack of a single reference makes it hard to find definitions for these acronyms. Microsoft Search solves that problem with Acronyms.

## What users experience

Microsoft Search users can get definitions with Acronyms in [Bing](https://Bing.com), [SharePoint](https://products.office.com/sharepoint/collaboration), [Office 365](https://Office.com), Outlook on the web, Outlook Mobile (Android), and Teams Mobile (iOS and Android). In the **Search** box, users enter queries like these examples:

- DNN
- *What is* DNN
- *Define* DNN
- DNN *definition*
- *Expand* DNN
- DNN *expansion*
- *Meaning of* DNN
- DNN *means*
- DNN *stands for*

The result includes all the meanings of DNN that are present within the user’s organization.

> [!NOTE]
> In Outlook on the web, Outlook Mobile, and Teams Mobile, users must enter a query that includes the acronym’s specified *keywords* to trigger its corresponding answers. Acronym queries are not case sensitive.

## Set up acronyms answers

In the [Microsoft 365 admin center](https://admin.microsoft.com), go to [**Acronyms**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/acronyms), and then select **Add acronym**.

Microsoft Search queries two data sources to provide Acronyms answers to users’ searches:

1. **Admin-curated**. Provided by IT administrators in the [admin center](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/acronyms).
2. **System-curated**. Discovered by Microsoft Search from users' email and documents, as well as publicly available data within the organization.

### Set up Admin-curated acronyms

Search administrators can add acronyms on the [Acronyms tab](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/acronyms) in the  [Microsoft Search admin center](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch). You can add acronyms from any internal site or repository to the admin center. These acronyms can be added to **Published** or **Draft** state:

**Published state**. Acronyms are available to the organization’s users through Microsoft Search.

> [!NOTE]
> It takes up to a day for acronyms added to Published state to become available in Microsoft Search.

**Draft state**. If you want to review an acronym before making it available in Microsoft Search, you can add the acronym in a Draft state. Acronyms in the Draft state don't appear in search results. You'll need to move the acronym to the Published state to make it appear in search results.

**Excluded state**. If you want to prevent an acronym from appearing in Microsoft Search, use **Exclude an acronym** to do so. To stop an acronym from being excluded, you'll need to delete the excluded acronym and add it or verify it's in your published list.

You can add acronyms individually or bulk import them in a CSV file. Upload a CSV file with the fields shown in the following table:

| Acronym (Mandatory) | Stands for (Mandatory) | Url | Description  | State (Mandatory) | Last Modified | Last Modified By | Id |
| --------- | --------- | --------- | ---------- | --------- |--------- |--------- |--------- |
| *XXX* | *Spelled out abbreviation* | *Source* |  | *Published, Draft, or Excluded* |  |  |  |

### CSV fields

**Acronym**. Contains the actual short form or acronym. An example is *DNN*.

**Stands for**. Contains the definition of the acronym. An example is *Deep Neural Network*.

**Description**. A brief description of the acronym that gives users more info about the acronym and its definition. For example, *A deep neural network is a neural network with a certain level of complexity, a neural network with more than two layers*.

**Source**. The URL of the page or website where you want users to go for more information about the acronym.

**State**. This field can take two values:

- **Draft**. Adds the acronym to the Draft state.
- **Published**. Adds the acronym to the Published state and makes it available in Microsoft Search.
- **Excluded**. Adds the acronym to the Excluded state and prevents it from appearing in Microsoft Search.

**Last Modified**. The date the acronym was last changed. Don't edit the data in this field.

**Last Modified By**. The user who made the last change to the acronym. Don't edit the data in this field.

**Id**. The unique identifier for the acronym. Don't edit the data in this field. If you include the ID of an existing acronym, it will be replaced with the information in the import file.

### System-curated acronyms

It might be a challenge for admins to add all the acronyms used within an organization to Answers. This feature can find acronyms that search administrators aren’t even aware of. To do that work, Microsoft Search also discovers and curates acronyms from these sources:

- Users’ emails
- Documents in [SharePoint](https://products.office.com/sharepoint/collaboration), [Microsoft OneDrive]( https://onedrive.live.com/about/), and [Microsoft OneNote](https://www.onenote.com/)
- Public documents within the organization that users have access to in SharePoint, OneDrive, or OneNote

Microsoft Search makes sure that only users with access and permissions to a document can see the acronyms that are discovered from it. When an acronym is found in a user's mailbox, only that user can see that acronym.

> [!NOTE]
> No setup is needed for system-curated acronyms.

## Frequently asked questions

**Q: How is admin-curated and system-curated data ranked?**

**A:** The ranking of results may vary from person to person as results are personalized for each user. Neither of these categories will always take precedence over the other.

**Q: How do users trigger acronyms answers?**

**A:** To get acronyms answers, users must enter specific query patterns in a [Bing](https://bing.com), [SharePoint](https://products.office.com/sharepoint/collaboration), [Office 365](https://Office.com), Outlook on the web, Outlook Mobile (Android), or Teams Mobile (iOS and Android) **Search** box.

**Q: Can users enter just the acronym when searching?**

**A:** On Bing, SharePoint, and Office 365 users can now find acronym answers just by searching for an acronym, a keyword is no longer needed. This same experience will be enabled for other Microsoft Search entry points in phases.

**Q: How long does it take for admin-curated acronyms to be visible in Microsoft Search after they’re published?**

**A:** It takes up to a day for acronyms added to Published state to become available in Microsoft Search.

**Q: How long does it take for system-curated acronyms to appear after you receive or send a new email or document?**

**A:** Acronyms found in a new email or document take up to seven days to appear in Microsoft Search results.

**Q: What happens when an acronym is both excluded and published?**

**A:** The excluded acronym is given priority and prevents the published acronym from appearing in search results. It doesn't delete or remove the published acronym.

**Q: How long does it take for an acronym to be excluded from Microsoft Search results?**

**A:** It takes up to a day for an excluded acronym to stop appearing in search results.

**Q: For system-curated acronyms, do documents need to be in a specific format?**

**A:** No. We support all file types except image, folder, and zip files.

**Q: Will Microsoft discover acronyms from documents in all languages?**

**A:** Microsoft only supports system-curated acronyms from documents in English, Spanish, French, Italian, German, and Portuguese. Support for other languages will be added in phases.

**Q: What if my organization doesn’t want to show system-curated acronyms? Can I stop showing this type of acronym in my search results?**

**A:** To turn off showing system-curated acronyms in search results, create a customer support ticket by following the instructions at [Contact support for business products](/microsoft-365/admin/contact-support-for-business-products).
After you create a support ticket, it takes up to 48 hours for system-curated acronyms to stop appearing in search results.

**Q: Are there any special considerations for naming Acronyms?**

**A:** Acronyms can't contain spaces. The acronym needs to be a contiguous string. If the acronym entered contains a space, it will be listed under Acronyms in the Search & intelligence admin portal, but the desired response will not be returned when a search is executed. For example, “Helpdesk” is an acceptable acronym but “Help desk” isn't.
