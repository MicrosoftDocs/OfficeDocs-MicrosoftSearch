---
title: "Manage Acronyms Answers in Microsoft Search"
ms.author: v-pamcna
author: TrishaMc1
manager: mnirkhe
ms.date: 10/10/2019
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Priority
search.appverid:
- BFB160
- MET150
- MOE150
description: "Overview of admin management of Acronyms Answers."
---

# Manage Acronyms Answers in Microsoft Search
Employees often run into unfamiliar acronyms and abbreviations that are used within their organization or teams. Organization-specific or team-specific terms might be new to people who move from one team to another, those who work with internal partner teams, or new employees.

Some employees might be hesitant to ask for definitions of these acronyms and abbreviations for fear of sounding ignorant. At other times, an organization doesn’t have a source of reference for its standard terminology. Microsoft Search solves that problem  with its Acronyms Answers feature.

## What users experience
Azure Active Directory (Azure AD) signed-in employees can get definitions with Acronyms Answers in [Bing](https://Bing.com), [Microsoft Office](https://Office.com), and [Microsoft SharePoint online](https://microsoft.sharepoint.com). In the **Search** boxes in the header bars, users enter queries like these examples:

- *What is* ABC
- *Define* ABC
- ABC *definition*
- *Expand* ABC
- ABC *expansion*
- *Meaning of* ABC
- ABC *means*

The suggested results include all the meanings of ABC that are present within the user’s organization.

> [!NOTE]
> Users must enter a query that includes the acronym’s specified *keywords* to trigger its corresponding Answers. 
 
## Set up Acronyms Answers in your organization
Microsoft Search queries two data sources for Acronyms Answers to users’ searches:

1. **Editorial Acronyms**. Provided by IT administrators in the [Admin portal](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch).

2. **Mined Acronyms**. Mined by Microsoft Search from the user’s personal email and documents and also from publicly available data within the organization.

### Set up Editorial Acronyms
IT admins can set up Editorial Acronyms within the    [Acronyms tab](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch). They can add acronyms from any internal site or repository to the **Admin** portal. Editorial Acronyms can be added to **Published** or **Draft** state:

**Published state**. Acronyms are available to the organization’s employees through Microsoft Search.

> [!NOTE]
> It takes up  to three days for acronyms added to Published state to become available in Microsoft Search.

**Draft state**. If admins want to review Acronyms Answers before making them available in Microsoft Search, they can add acronyms to Draft state. Acronyms added to Draft state aren’t available in Microsoft Search. Admins need to add the Acronyms to Published state to make them available.

Admins can add acronyms individually or bulk import them in a CSV file. Upload a CSV file with the fields shown in the following table:

| Acronym (mandatory) | Expansion (mandatory) | Description  | Source | State (mandatory) |
| --------- | --------- | ---------- | --------- |--------- |
| *XXX* | *Spelled out abbreviation* |  | *URL* | *Published or Draft* |


> [!NOTE]
> As specified in the CSV column names, you must add the Acronym, Expansion, and State fields.

### CSV fields
**Acronym**. Contains the actual short form or acronym. An example is ABC.

**Expansion**. Contains the expansion of the acronym. An example is the American Ballet Center.

**Description**. A brief description of the acronym that gives users quick insight into what the acronym and its expansion really mean. For example, *The American Ballet Center is the premier institute for ballet dance training in America*.

**Source**. The URL of the page or website where you want users to go for more information about the acronym.

**State**. This field can take two values:

- **Draft**. Adds  the acronym to the Draft state.

- **Published**. Adds the acronym to the Published state and makes it available in Microsoft Search.

### Mined Acronyms
Microsoft Search understands that Editorial Acronyms data gets stale without maintenance. Also, many acronyms used within teams might be relevant to users, but admins might not add them to the Editorial Acronyms data. To resolve those issues, Microsoft Search mines acronyms from additional sources:

- Users’ own emails and documents in SharePoint, OneDrive, and OneNote.

- Public documents within the organization that users have access to in SharePoint, OneDrive, or OneNote.
Microsoft Search makes sure that only users with access and permissions to a document can see the acronyms that are mined from it. 

> [!NOTE]
> No IT admin setup is needed for Mined Acronyms.
## Frequently asked questions
**Q:** **How is Editorial and Mined data ranked?**

**A:** The feature currently ranks Editorial Acronyms above Mined Acronyms.

**Q:** **How long does it take for Editorial Acronyms to be visible in Microsoft Search after they’re published?**

**A:** After they’re added to the Published state, Editorial Acronyms are available in Microsoft Search within a few hours. 

**Q**: How do users trigger Acronyms Answers?

**A**: To get Acronyms Answers, users must enter specific query patterns in a SharePoint, OneDrive, or OneNote **Search** box. Examples of queries that find answers for the term *ABC* are as follows:

- *What is* ABC
- *Define* ABC
- ABC *definition*
- *Expand* ABC
- ABC *expansion*
- *Meaning of* ABC
- ABC *means*

**Q:** **Will Mined Acronyms be available to my organization?**

**A:** Yes. Mined Acronyms are turned on by default. 

**Q:** **How long does it take for Mined Acronyms to appear after you receive or send a new email or document?**

**A:** Mined Acronyms from a new email or document take up to seven days to appear in Microsoft Search results. 

**Q**: **Do documents need to be in a specific format for mining to pick them up?**

**A:** No. Mining works on all your emails and documents in any format they’re in. 

