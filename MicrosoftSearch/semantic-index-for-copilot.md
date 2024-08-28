---
title: "Semantic index for Copilot"
ms.author: camillepack   
author: camillepack
manager: scotv
ms.topic: overview
ms.service: microsoft-365-copilot
audience: Admin
ms.audience: Admin
ms.date: 08/27/2024 
ms.localizationpriority: medium
ms.collection:
- scotvorg
- m365copilot
- magic-ai-copilot
description: "Learn about Semantic index for Microsoft Copilot."
---

# Semantic index for Copilot

Semantic index is generated from content in [Microsoft Graph](https://developer.microsoft.com/graph). It's used to aid in the production of contextually relevant responses to user queries. It allows organizations to search through billions of vectors (mathematical representations of features or attributes) and return related results. Combined with enhancements across the Microsoft Graph, semantic index connects you with relevant information in your organization. It's built on Microsoft’s comprehensive approach to [security, compliance, privacy](/microsoft-365-copilot/microsoft-365-copilot-privacy), and respects all organizational boundaries within your tenant.

## What is an index?

The concept of indexing data is well established in Microsoft 365. Indexing is one of the important ways that Microsoft 365 services access the tremendous amount of data in Microsoft Graph, where your Microsoft 365 tenant resides. With indexing, users see search results from Microsoft Graph, including content and signals from most Microsoft 365 applications in your tenant. This ensures that search results are personalized and elevated based on your connections between content and people in your network.

Interactions with data in Microsoft Graph are based on keyword matching, personalization, and social matching. Keyword search queries against an index in the Microsoft Graph, which maps to locations in documents or a set of documents. Microsoft 365 uses the Microsoft Graph to rank the most relevant content based on its knowledge of additional signals for users and their close network. This is known as personalization and social matching in Microsoft 365, which drives relevance for queries against the content in your organization. Access to tenant data in Microsoft Graph is gated by role-based access control. Organizations are always in control of Microsoft Search capabilities via the Search and Intelligence portal in the Microsoft 365 admin center.

## How the semantic index helps manage your data

Semantic index enhances the features of Microsoft 365 that allow you to find relevant content based on keywords, personal preferences, and social connections. It does this by creating vectorized indices. A vector is a numerical representation of a word, image pixel, or other data point. The vector is arranged or mapped with close numbers placed in proximity to one another to represent similarity. Vectors are stored in multi-dimensional spaces where semantically similar data points are clustered together in the vector space, enabling Microsoft 365 to handle a broader set of search queries beyond “exact match."

In practical terms, this means that Microsoft 365 services such as Copilot for Microsoft 365 can:

- Understand relationships between different forms of words (for example, tech, technology, technologies; USA, U.S.A, United States, United States of America; dog, cat, pet).
- Capture synonyms to expand the amount of searchable information, including the intent of sentences, snippets, documents, and meetings.
- Identify related assets to your query or sample content.

The following graphic uses text (instead of numbers used by vectorized indices) to show an example of similarity between data points:

:::image type="content" source="media/semantic-index-vector-example.png" alt-text="Graphic showing an example of how data points for Semantic Index are clustered together.":::

Semantic index provides for fast and accurate similarity search and retrieval of data based on their vector distance or similarity. This means that in addition to using traditional lexical methods for querying based on exact matches or predefined criteria, the semantic index can find the most similar or relevant data based on the semantic or contextual meaning.

## Features

The following semantic index features do more than enhance search results; they work together to help you understand your data, find information more quickly, and improve your productivity. Users can interact with the semantic index initially through Microsoft Copilot for Microsoft 365 integration. We generate a semantic index for users with a paid Copilot for Microsoft 365 license. Here are the details of how each feature works.

### Microsoft Copilot with Graph-grounded chat

Semantic index helps surface results within Microsoft Copilot with Graph-grounded chat by understanding the intent of your query and appending additional information to your Microsoft Copilot prompt. Relevant information is obtained in the Microsoft Graph and semantic index to provide the large language model (LLM) with more information to reason over. As an example, suppose you want Microsoft Copilot to locate an email where a colleague praised the design work of a vendor. Semantic index includes nearby words (for example, elated, excited, amazed) into the search to broaden the search area and give the best result. All of this work takes place behind the scenes to add relevance to results that you search for with Microsoft Copilot, without adding complexity.

## How the semantic index works

Semantic index enhances Microsoft Copilot and search results in the [Microsoft 365 app](https://www.microsoft365.com/), SharePoint Online, and Microsoft Teams. It supports an enhanced search experience and conceptual understanding of your online data that is automatically enabled by Microsoft.

Today, semantic index is created at the tenant level. It's an organization-wide index generated from text-based SharePoint Online files that are accessible by two or more people via site inheritance. However, it only surfaces the results to a user if the user already has access to the content controlled by role-based access control. Additionally, the SharePoint Online site must remain searchable. In time, we'll also generate user-level index content. This adds personalized index of a working set of data that is accessible for users performing everyday tasks. This includes any text-based content you make or interact with, such as emails, documents that mention you, or that you comment on or share.

The following section explains how to enable each index, how the data flow in Copilot for Microsoft 365 uses the semantic index, what file types each index can handle, and how each index deals with updates.

## Enablement

Every Copilot for Microsoft 365 customer now has a tenant-level semantic index. The indexing process requires no administrative involvement.

## Data flows

The semantic index interacts with the Microsoft Graph to provide users with access to information in the index. The following diagram shows how the flow of data works for a request using Copilot for Microsoft 365.

:::image type="content" source="media/copilot-architecture.png" alt-text="Graphic showing the relationship between Copilot for Microsoft 365, Microsoft 365 Apps, Microsoft Graph, and Large Language Model." lightbox="media/copilot-architecture.png":::

User prompts from Microsoft 365 apps are sent to Copilot (1), and Copilot accesses the Microsoft Graph and semantic index for processing (2). Copilot sends the modified prompt to the Large Language Model (3), receives the LLM response (4), and then accesses the Microsoft Graph and semantic index for post-processing (5). Copilot then sends the response and app command back to Microsoft 365 apps. All requests are encrypted by HTTPS and customer data remains encrypted at rest.

## Supported content types

The semantic index supports indexing of user mailbox and file types listed in the following table, with more file types supported over time. A list of supported file types for the user-level index and tenant-level index is included in the table.

|   Content/file type       |   User level   |   Tenant level   |
|---------------------------|----------------|------------------|
| User Mailbox              | Supported      | Not applicable   |
| Delegated Mailbox         | Not supported  | Not applicable   |
| Shared Mailbox            | Not supported  | Not applicable   |
| Archived Mailbox Data     | Not supported  | Not applicable   |
| Archived SharePoint Data  | Not supported  | Not supported    |
| Word documents (doc/docx) | Supported      | Supported        |
| PowerPoint (pptx)         | Supported      | Supported        |
| PDF files                 | Supported      | Supported        |
| Web pages (aspx)          | Supported      | Supported        |
| OneNote files (one)       | Supported      | Supported        |
| Graph Connector data      | Not applicable | Supported        |

## Index updates

When Semantic index completes indexing for a customer for the first time, documents created by users are indexed in near real-time in the user's mailbox. New documents that are added to SharePoint Online sites that are accessible, via site inheritance, by two or more users are indexed daily. When an indexed user and tenant level document is updated, the changes are immediately indexed.

## Administration

We provide administrators with optional activities to prepare and manage the semantic index via the Microsoft 365 admin center. There's no administrative involvement required to enable the semantic index, as the service is automatically enabled by Microsoft. Semantic index is an improvement to Microsoft 365 Search and can't be disabled.

Administrators can choose to prepare and manage the semantic index by reviewing the considerations for [planning and deploying a file collaboration in SharePoint](/sharepoint/deploy-file-collaboration) and [sharing permissions in the SharePoint modern experience](/sharepoint/modern-experience-sharing-permissions). Administrators can choose to exclude files from the semantic index by reviewing the considerations for excluding data with Microsoft Purview Data Loss Prevention (DLP). If a DLP solution isn't present, administrators can exclude SharePoint Online sites from the tenant level index.  

## Excluding SharePoint Online Sites

There are times when organizations without Microsoft Purview Data Loss Prevention might want to exclude a SharePoint Online site from having its data indexed by Microsoft Search. These steps should only be considered for sensitive data, such as payroll, HR, or financial information. To exclude a SharePoint Online site, follow these steps:

1. Browse to the site with appropriate administrator permissions.
1. Select **Settings** then **Site information** from the drop-down menu.
1. Select **View all site settings** to bring up the Site Settings page.
1. Select **Search and offline availability** under the **Search** category and select **No** for **Allow this site to appear in search results** to exclude it from both Microsoft Search and the semantic index search. This can also be performed with PowerShell for multiple sites.

:::image type="content" source="media/semantic-index-settings.png" alt-text="Screenshot showing the settings for excluding SharePoint online sites." lightbox="media/semantic-index-settings.png":::

Microsoft Search and the semantic index support the exclusion of SharePoint online content from the tenant-level index only. There's no option to exclude results from Microsoft Search only or the semantic index only; actions apply to both at the same time.

## Configuring item insights

On the Search and Intelligence page in the Microsoft 365 admin center, Item insights are enabled by default. Turning off people or item insights reduces the Microsoft Search and semantic index experience, as results won't include relevant people that would have been derived from distribution groups or from the organizational chart.

- **People insights** provide a list of relevant people to a user based on their public collaborative work in Microsoft 365. Public collaboration includes members of a public distribution group and individuals connected in the organizational chart.

- **Item insights** allow recommendations for people in your organization based on their collaborative work in Microsoft 365. These recommendations might include but aren't limited to documents or other types of content and show up in people cards (contacts), Delve, The [Microsoft 365 app](https://www.microsoft365.com/), Microsoft Copilot results, and other locations.

Both Item insights and People insights don't cover personalization features based on a user's own data.

## Incorporating third party information

Using Copilot Connectors, organizations can bring organizational data or content from external sources into Microsoft Graph, where it's then brought into semantic index. Microsoft indexes all your Graph connectors data while maintaining access controls for content. This expands the types of content sources that are searchable in your Microsoft 365 productivity apps and the broader Microsoft ecosystem, and works best when connector content is text rich. The third-party data can be hosted on-premises or in the public or private clouds, and this information is consumed by the Microsoft Graph, which can be ingested into the semantic index to help provide your organization with all the context across Microsoft 365 and your organization’s third party content. Learn more about graph connector licensing requirements for Microsoft 365 Enterprise and Copilot for Microsoft 365 at [License requirements and pricing](licensing.md).

## Privacy, compliance, and security

The permissions model within your Microsoft 365 tenant can help ensure that data won't unintentionally leak between users, groups, and tenants. Semantic index presents only data that each individual can access using the same underlying controls for data access used in other Microsoft 365 services. Semantic index honors the user identity-based access boundary so that the grounding process only accesses content that the current user is authorized to access. For more information, see [Microsoft’s privacy policy and service documentation](https://privacy.microsoft.com/).

Microsoft Copilot for Microsoft 365 is compliant with our existing privacy, security, and compliance commitments to Microsoft 365 commercial customers, including the General Data Protection Regulation (GDPR) and European Union (EU) Data Boundary. Prompts, responses, and data accessed through the semantic index aren't used to train foundation LLMs, including those used by Copilot for Microsoft 365. For more information, see [Data, Privacy, and Security for Copilot for Microsoft 365](/microsoft-365-copilot/microsoft-365-copilot-privacy).

## Storage and processing

Data generated by the semantic index remains within your company’s tenant, and complies with your security, compliance, identity, and privacy policies and processes. The semantic index works only with content to which your users already have permission and doesn't affect storage quotas.

User-level index information is stored where the user's mailbox is located. Tenant-level index information, on the other hand, is stored in an isolated and protected customer’s tenant container. This container is located in the region where the SharePoint site is located, which can be the Home region or another region specified by the tenant admin. For customers within the European Union Data Boundary (EUDB), the index is stored in an EU/EFTA based datacenter. Processing other customers can take place either in a tenant region or in the United States. For multi-geo organizations, all geographical boundaries are respected. In-region data is stored and processed in each region.

## Microsoft Purview Customer Key (BYOK) support

The semantic index provides bring your own key (BYOK) support for enterprises that have enabled BYOK in their environment. Microsoft automatically enables the semantic index for BYOK enabled customers without any administrative involvement.

## Information protection

In the context of search, there are no other ways to exclude data from the semantic index using information protection capabilities. The semantic index inherits security and privacy settings from Microsoft Search, and data brought in from third party connectors are provided the same storage and protections as other Microsoft 365 data. For organizations that are investigating additional information protection options, Microsoft 365 provides built-in capabilities in Microsoft 365 apps. Add-on products are also available to help Administrators protect organizational data through data minimization and reducing oversharing. The following sections outline the options available for organizations for reference only.

## Data minimization

Data minimization reduces the amount of available data your organization might access. Retaining and deleting content is often needed for compliance and regulatory requirements, but deleting content that no longer has business value also helps you manage risk and liability. [Microsoft Purview Data Lifecycle Management](/purview/data-lifecycle-management), which is [licensed separately](https://azure.microsoft.com/products/purview/), can be used to delete content that is no longer needed with retention policies for management at scale, and retention labels for exceptions and granular control.

## Reduce oversharing

Organizations have long been able to take action to reduce oversharing in Microsoft 365 using existing controls in the Microsoft 365 admin center and SharePoint Online. It's important to note that semantic index doesn't change access permissions to content and doesn't change the principles of how users should share information with colleagues. For example, the semantic index doesn't make content shared with a link that works with everyone in my organization part of the tenant level index. Only users that select a link that they have access to will have the information added to their user index. It's recommended that organizations consider the following when exploring information protection options:

- **Plan secure file collaboration** – Review [Plan and deploy a file collaboration](/sharepoint/deploy-file-collaboration) to understand more about recommended practices to operate a secure and productive file collaboration environment for your users.

- **Right size user access to data to reduce the list** – reduce oversharing by inheriting exclusion lists for SharePoint Online sites and performing access control checks in real time. Organizations can consider using the [Syntex SharePoint Advanced Management add-on](/sharepoint/advanced-management) to manage and govern these permissions.

- **Use sensitivity labels** - Another way to reduce content oversharing is to use [Microsoft Purview Information Protection](/purview/information-protection) to apply sensitivity labels, which allow you to classify data based on its sensitivity, and apply protections like encryption and content marketing. Sensitivity labels  are also included in search trimming (that is, supported for filtering and application-side rules used for visual marking and access restrictions).

- **Limit access** – [Microsoft Purview Data Loss Prevention](/purview/dlp-learn-about-dlp) is available in Microsoft 365 E5 and could be used to retroactively and temporarily limit access to documents that have been reported as overshared. Organizations that you do not have Microsoft 365 E5 licenses can use the 90-day Microsoft Purview solutions trial to explore how additional Purview capabilities can help manage your data security and compliance needs.

For customers interested in exploring how to deploy advanced information protection solutions, review the following article that explains how to [deploy an information protection solution with Microsoft Purview](/purview/information-protection-solution). For more information about how Microsoft Purview can help you strengthen your data security and compliance requirements for Copilot for Microsoft 365, see [Protect and manage Copilot for Microsoft 365 interactions with Microsoft Purview](/purview/ai-microsoft-purview).

## Additional resources

Microsoft 365, the Microsoft Graph, and the semantic index enable an unprecedented expressiveness for search, chat, and copilots leveraging Microsoft 365 data. This expressiveness helps surface the right grounding data to get the most out of your organizational data with Microsoft 365 and Copilot for Microsoft 365.

To learn more about Copilot for Microsoft 365, check out these resources:

- [Get started with Copilot in Microsoft 365](/microsoft-365-copilot/microsoft-365-copilot-setup)
- [Data, Privacy, and Security for Microsoft Copilot for Microsoft 365](/microsoft-365-copilot/microsoft-365-copilot-privacy)
- [Microsoft Copilot for Microsoft 365 adoption site](https://adoption.microsoft.com/copilot/)
