---
title: "Manage access to files and sites"
ms.author: davidedwards
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
description: "An overview of how administrators can ensure access to sites and files are properly restricted within their organization."
ms.date: 08/05/2021
---

# Manage access to files and sites

Not every file or site should be available to everyone in your organization. Administrators and users can manage access to sensitive or confidential info using solutions that best address their specific issues. If adequate access controls aren't consistently applied, it can result in something we refer to as 'oversharing.' By making it easier to find information shared within your organization, files and sites with improper restrictions can be inadvertently accessed using Microsoft Search.

Search admins can't resolve these oversharing issues. Files and sites without restricted access will be surfaced in internal search results and through other avenues of discovery. However, when controls to prevent oversharing are in place, all avenues, including search, will be closed.

## Solutions to prevent oversharing

Use the tools, policies, and techniques below to restrict or obfuscate access to information to help prevent oversharing. Implementing these solutions will likely require Global, Compliance, or Security admin access. We also recommend an internal campaign to educate your users about how to properly secure, label, and permission their sites and files.

### Public sites or sites with public groups as owners

One way files can be shared with everyone is through public sites or sites with public groups as owners. Sensitivity labels can prevent users from creating public groups or sites. For details about configuring all labels to create private groups/sites and mandating a label for groups/sites, see [Use sensitivity labels to protect content in Microsoft Teams, Microsoft 365 Groups, and SharePoint sites](/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).

Another option is to control who can create Microsoft 365 Groups in your organization. For more information, see [Create a group for users who need to create Microsoft 365 Groups](/microsoft-365/solutions/manage-creation-of-groups#step-1-create-a-group-for-users-who-need-to-create-microsoft-365-groups).

When implementing either of these solutions, we also suggest you set up a process for users to request creation of public groups and inform your users about the change.

If restricting the ability to create groups isn't possible for your organization, you can monitor activities, including group creation, through auditing. For details about basic and advanced auditing, see [Auditing solutions in Microsoft 365](/microsoft-365/compliance/auditing-solutions-overview).

### Shared files

To restrict access to all files classified as business sensitive, you can define and apply data classifications for your organization. Sample data will need to be collected to help train new classifiers. For details about prerequisites and permissions, see [Learn about data classification](/microsoft-365/compliance/data-classification-overview).

To restrict file access to members of a specific group, like executives, you can create custom labels scoped to a security group. Then, when a security group member applies the label, it automatically restricts access to the group. To learn more about custom labels, see [Create and configure sensitivity labels and their policies](/microsoft-365/compliance/create-sensitivity-labels) and [Restrict access to content by using sensitivity labels to apply encryption](/microsoft-365/compliance/encryption-sensitivity-labels).

To ensure documents and emails are properly labeled, admins can also set a default label policy and require users to label them. For more information, see [Require users to apply a label to their email and documents](/microsoft-365/compliance/sensitivity-labels-office-apps#require-users-to-apply-a-label-to-their-email-and-documents).

You can also minimize file oversharing by preventing recent files from appearing when searching. This can be done on a group level or for everyone in your organization. To stop recent files from appearing for a group, see [Customizing item insights privacy in Microsoft Graph](/graph/insights-customize-item-insights-privacy). A group member will be able to see their own recent files, but others will get a message that no results are found. To turn off recent files for everyone in your organization, you'll need to turn off Delve. For details, see [Control access to Delve](/sharepoint/delve-for-office-365-admins#control-access-to-delve).

> [!Note]
> Users will still be able to find files shared with them in Microsoft Search results. Customizing item insights or turning off Delve only stops files from appearing in a user's list of recent files.

### Sites and files between groups

To restrict file and site sharing between groups, for example, a finance team that manages confidential projects with a marketing team, you can define and implement information barrier policies. These barriers also prevent other aspects of communication and collaboration in Microsoft Teams, SharePoint, and OneDrive. For details, see [Learn about information barriers in Microsoft 365](/microsoft-365/compliance/information-barriers).

## Get access insights

Access governance provides insights about sites with the most sensitive documents and overshared sites in your organization. For an overview, see [What's new in Security and Compliance in SharePoint and OneDrive](https://techcommunity.microsoft.com/t5/microsoft-sharepoint-blog/what-s-new-in-security-and-compliance-in-sharepoint-and-onedrive/ba-p/1696705). You'll need to [nominate your organization](https://forms.microsoft.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR3-O9WDTKhhDtgWfphwS9YhUM0hJNklNRkZKMlhLNDRZNzlEQlVDSjdZVi4u) for this preview.
