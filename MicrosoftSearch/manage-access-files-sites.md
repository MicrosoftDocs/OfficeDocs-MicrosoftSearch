---
title: "Manage access to files and sites"
ms.author: dawholl
author: dawholl
manager: kellis
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
  - BFB160
  - MET150
  - MOE150
description: "Get an overview of how Global admins can ensure confidential or sensitive info isn't overshared within their organization."
---

# Manage access to files and sites

Not every file or site should be available to everyone in your organization. Global admins and users can manage access to sensitive or confidential info using a variety of solutions to address specific issues. If adequate access controls aren't consistently applied, it can result in oversharing. By making it easier to find info shared within your organization, files and sites that aren't properly permissioned or restricted can be inadvertently accessed using Microsoft Search.

## Solutions to prevent oversharing

Use the tools, policies, and techniques below to restrict or obfuscate access to info, to help prevent oversharing. Implementing these solutions will require likely Global, Compliance, or Security admin access.

### Public sites or sites with public owners

One way that files can be shared with everyone in your organization is through the use of public sites or sites with public owners. Sensitivity labels can prevent users from creating public groups or sites. This is done by configuring all labels to create private groups and require a label for groups. For details, see [Use sensitivity labels to protect content in Microsoft Teams, Microsoft 365 groups, and SharePoint sites](/microsoft-365/compliance/sensitivity-labels-teams-groups-sites). You'll need to define a separate process for users to request or create public groups.

Another option is to define who can create Microsoft 365 groups in your organization. See [Create a group for users who need to create Microsoft 365 groups](/microsoft-365/solutions/manage-creation-of-groups?view=o365-worldwide#step-1-create-a-group-for-users-who-need-to-create-microsoft-365-groups) for more information. A global admin will need to set up a process for users to submit group creation requests. We also suggest you inform users about this change.

If restricting the ability to create groups isn't viable for your organization, you can monitor activity, including group creation, through auditing. For details about basic and advanced auditing, see [Auditing solutions in Microsoft 365](/microsoft-365/compliance/auditing-solutions-overview?view=o365-worldwide).

### Shared files

To restrict access to all files classified as business sensitive, you can define and apply data classifications for your organization. Sample data will need to be collected to help train new classifiers. For details about prerequisites and permissions, see [Learn about data classification](/microsoft-365/compliance/data-classification-overview).

To restrict files access to members of a specific group, executives for example, you can create custom labels scoped to a security group. When a security group member applies the custom label it automatically restricts access to members of the group. To learn more about custom labels, see [Create and configure sensitivity labels and their policies](/microsoft-365/compliance/create-sensitivity-labels) and [Restrict access to content by using sensitivity labels to apply encryption](/microsoft-365/compliance/encryption-sensitivity-labels).

To help ensure documents and emails are properly labeled, admins can also set a default label policy and require users to apply labels to their files and emails. For more information, see [Require users to apply a label to their email and documents](/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide#require-users-to-apply-a-label-to-their-email-and-documents).

You can also minimize file oversharing by preventing recent files from appearing when users search for other people in the organization. This can be done on a group level or for everyone in your organization. To stop recent files from appearing for a group, see [Customizing item insights privacy in Microsoft Graph](/graph/insights-customize-item-insights-privacy). A user in the group will be able to see their own recent files, but others will get a message that no results are found. To turn off recent files for everyone in your organization, you'll need to turn off Delve. For details, see [Control access to Delve](/sharepoint/delve-for-office-365-admins#control-access-to-delve).

> [!Note]
> Users will still be able to find files shared with them in Microsoft Search results. Customizing item insights or turn off Delve only stops files from appearing in a user's list of recent files.

### Sites and files between groups

If you need to restrict the sharing of files and sites between groups, for example, a finance team working on confidential projects and a marketing team, you can define and implement information barrier policies. These barriers also prevent other aspects of communication and collaboration in Microsoft Teams, SharePoint, and OneDrive. For details, see [Learn about information barriers in Microsoft 365](/microsoft-365/compliance/information-barriers).

## Get access insights

Access governance insights for SharePoint, OneDrive, and Teams provides data about sites with most sensitive documents and over shared sites in your organization. For an overview, see [What's new in Security and Compliance in SharePoint and OneDrive](https://techcommunity.microsoft.com/t5/microsoft-sharepoint-blog/what-s-new-in-security-and-compliance-in-sharepoint-and-onedrive/ba-p/1696705). You'll need to [nominate your organization](https://forms.microsoft.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR3-O9WDTKhhDtgWfphwS9YhUM0hJNklNRkZKMlhLNDRZNzlEQlVDSjdZVi4u) for this preview.

## Frequently asked questions

**Q: Can I disable Microsoft Search in Bing?**

**A:** You can turn off Microsoft Search in Bing on the [Configurations](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/configurations) page in the Microsoft admin center. Choose **Change settings** and turn off **Allow your organization to use Microsoft Search in Bing**. When this setting is off, users won't get internal results when they search from Bing, Windows Search, or Microsoft Edge. They also won't see information from your organization when they go to the Bing homepage. It takes up to 24 hours for this change to take effect.

Turning off Microsoft Search in Bing doesn't stop or prevent internal content from being added to your search index. It only disables Bing entry points to Microsoft Search. To find answers and internal results, users will need to use other entry points, for example SharePoint Online and or an Office 365 app. It also doesn't prevent oversharing, files and sites that aren't properly permissioned or restricted will still be accessible.
