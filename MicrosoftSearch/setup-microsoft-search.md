---
title: "Set up Microsoft Search"
ms.author: anfowler
author: adefowler
manager: mnirkhe
ms.date: 05/30/2019
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Priority
search.appverid:
  - BFB160
  - MET150
  - MOE150
description: "Set up Microsoft Search for the first time."
---

# Set up Microsoft Search

Microsoft Search provides a user-friendly interface to help users find information, like files and documents, internal sites and business tools, people and groups, locations and directions, conversations and answers by securely accessing all data sources, including emails, files, SharePoint files, OneDrive content, and other shared resources as well as the internet in the user’s organization.

To learn more about Microsoft Search features, see [Microsoft Search Overview](overview-microsoft-search.md).

## Get Started

Microsoft Search is turned on by default for all Microsoft apps that supports it, as a part of Microsoft 365. All a user needs to do is to sign-in with a work or school account and use a browser with Bing set as the default search provider.

You manage Microsoft Search from Microsoft 365 admin center.

1. In Microsoft 365 admin center, go to **Settings** > **Microsoft**.

**Note:** If you are NOT seeing Microsoft Search under **Settings**, turn on the **Try the preview** switch in the right top corner of any admin center page.

As an admin you should consider a few things that can make the Microsoft Search experience efficient and user friendly in your organization.

## Step 1: Check access level of your users

Microsoft Search respects security settings of the content source. What users see in their search result depends on their permissions and access levels. Review the access level of users in your organization to make sure that users only find content that they are allowed to access.

| Service         | Description                                                                                                                                                                                                                                         |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Groups          | [Add or remove members from groups](https://docs.microsoft.com/office365/admin/create-groups/add-or-remove-members-from-groups)                                                                                                                     |
| People          | You can hide certain users from being searched in your address list by setting the `HiddenFromAddressListEnabled` parameter to `true` using the [Set-User](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/set-user) cmdlet. |
| Microsoft Teams | [Manage user access to Microsoft Teams](https://docs.microsoft.com/microsoftteams/user-access)                                                                                                                                                      |
| OneDrive        | [Manage sharing](https://docs.microsoft.com/OneDrive/manage-sharing)                                                                                                                                                                                |
| SharePoint      | [Planning permissions](https://docs.microsoft.com/en-us/sharepoint/plan-your-permissions-strategy)<br> [Creating permissions levels](https://docs.microsoft.com/en-us/sharepoint/how-to-create-and-edit-permission-levels)                          |
| OneNote         | You can't search on files that are embedded in OneNote. [Change permissions for a notebook on OneDrive](https://support.office.com/article/B9600CCF-045A-40E6-9913-4A7EB02869A5)                                                                    |
| Yammer          | [Yammer security settings](https://docs.microsoft.com/Yammer/manage-security-and-compliance/yammer-security-settings)                                                                                                                               |

## Step 2: Assign Search admin and Search editor

There are two limited admin roles to help you support Microsoft Search – **Search admin** and **Search editor**.

> [!NOTE]
> Search admin role and the Search editor role only grant permissions in the Microsoft 365 admin center, not the legacy **Microsoft Search in Bing admin portal**. You need to be a global admin to manage Microsoft Search in the legacy portal.

Search admins directly influence the search experience for end users. This includes choosing the types of results you want to surface to your users. It may be difficult for one person to choose and create authoritative content on many different topics that users search for in an organization. We recommend that you leverage the expertise and knowledge of subject matter experts (SME) and other users by adding them as Search editors.

In Microsoft Search, you can manage your organization’s search settings and content by assigning these roles to users:

1. **Search admin:** This role can create and manage search result content and define query settings for improved search results within the organization. Search admin manages the Microsoft Search configuration and designates Search editors to create content.
2. **Search editor:** Creates, manages, and deletes content for Microsoft Search in the Microsoft 365 admin center. This role can create and manage editorial content, such as frequently asked questions and answers, important places and locations, frequently searched and used sites and apps.

For assigning admin roles, see [Assign admin roles](https://docs.microsoft.com/en-us/office365/admin/add-users/assign-admin-roles?view=o365-worldwide).

## Step 3: Make content easy to find

Microsoft Search provides administrators with tools that they can use to build a robust search experience for their users. In Microsoft Search, administrators have three different search contents that they can create for a better search experience and to improve the findability of content:

- **Bookmarks:** Bookmarks are similar to promoted results in SharePoint and help promote the best possible results for your user's queries to the top of the search results and make it easy for your users to find important internal sites.
- **Questions & Answers:** Q&A are similar to frequently asked questions and these are usually in a question and answer format. It provides the best possible answer(s) to your user's work-related questions.
- **Locations:** Locations are addresses that help users locate your organization's buildings, offices, and campuses.

The more Bookmarks, Q&A, and Locations you have, the more value and benefit you add for users. However, too many of them can add a substantial management overhead as they must be reviewed and updated periodically to keep the results relevant and up to date.

Here are some examples of content that you should consider bookmarking for your users:

- Organization or product or service information.
- Informational content that is available for everyone; for example, information about the company, help for Windows and Office apps, etc.
- Content that people in the organization generally search for in their day-to-day work. Common work-related searches include employee benefits, time and expense reporting, submitting purchase orders, and getting help from IT services.

For creating and managing search content, see [Make content easy to find](make-content-easy-to-find.md).

## Step 4: Test single sign-on

Microsoft Search uses Azure Active Directory (AAD) to authenticate and authorize access to your organization’s data. This means your users are automatically signed in with your work or school account when you've signed into an Office 365 app or Windows 10.

We recommend that Microsoft Search users use single sign-on as it reduces the number of times users are prompted to sign in. Administrators should test single sign-on with a small group of users to help identify any blocking configuration issues.

For Chrome users on Windows 10, single sign-in works only when the Windows 10 and AAD sign-in extension for Chrome is installed. Once installed, you can use the Chrome extension to easily authenticate with AAD when signing in to supported sites, including Office 365 and Bing. This functionality is available for authorized users only.

To download and install Windows 10 and AAD sign-in extension for Chrome, go to [Chrome Web Store](https://go.microsoft.com/fwlink/?linkid=2090961).

## Step 5: Training and communication

Establish self-service resources that employees can easily access on their own. This will help reduce the overall burden on you and your team to constantly push communications and assist in self-training and educating employees. Provide your users communications, FAQs, videos, and recorded training or webinars. Here are some helpful links to start with:

- [Find what you need with Microsoft Search in Office](https://support.office.com/article/find-what-you-need-with-microsoft-search-in-office-2457d4d8-48a8-4ad4-ab89-5a0657aa8446?ui=en-US&rs=en-US&ad=US)
- [Office 365 Training Center](https://support.office.com/office-training-center)
- [Microsoft Search Center](https://support.office.com/en-us/article/-working-title-microsoft-search-center-b8bf5a2c-7515-40a9-9a6a-b8ed382c86bc?ui=en-US&rs=en-US&ad=US)

## Trying out Microsoft Search in Bing

You can turn **Microsoft Search in Bing** off. If turned off, users will not see organization content in Bing search. By default, Microsoft Search in Bing is turned on.We recommend that you keep Microsoft Search turned on in Bing for a better user experience.

Go to **Settings** > **Services & add-ins** > **Microsoft Search in Bing** to turn it on or off.
