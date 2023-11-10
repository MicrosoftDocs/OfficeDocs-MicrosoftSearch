---
title: "Semantic Index for Copilot"
ms.author: camillepack   
author: camillepack
manager: scotv
ms.topic: article
ms.service: microsoft-365-copilot
audience: Admin
ms.audience: Admin
ms.date: 11/10/2023 
ms.localizationpriority: medium
ms.collection:
- scotvorg
description: "Learn about Semantic Index for Copilot."
---

# Semantic Index for Copilot

The semantic index brings a whole new world of understanding to your data in Microsoft 365. Through enhanced interactions with your individual and company data via the Microsoft Graph, and the creation of a new index, the semantic index is an improvement to Microsoft 365 search that lays the foundation for the next generation of Search and Copilot experiences. The semantic index respects security and policies in the Microsoft Graph so that when a user issues a query either directly via search or in Microsoft 365 chat via Copilot, it's always in the security context of the user, and only content that a user has access to is returned. This whitepaper reviews the initial set of features that form the semantic index and explains how it brings your data to life.

## Overview

The semantic index sits on top of the Microsoft Graph, which interprets user queries to produce sophisticated, meaningful, and multilingual responses that help you to be more productive. It allows organizations with Microsoft 365 Copilot, Microsoft 365 Business Standard, Business Premium, E3 and E5 to search through billions of vectors (mathematical representations of features or attributes) and return related results. Combined with enhancements across the Microsoft Graph, the semantic index connects you with relevant and actionable information in your organization and is built on Microsoft’s comprehensive approach to security, compliance, privacy, and respects all organizational boundaries within your tenant.

## What is an Index?

The concept of indexing data is well established in Microsoft 365 and is a normal part of how the Microsoft Graph works to access the tremendous amount of data in your Microsoft 365 tenant today. Users see search results from the Microsoft Graph, which indexes content and signals from most Microsoft 365 applications in your tenant to ensure search results are personalized and elevated based on your connections between content and people in your network. Interactions with data in the Microsoft Graph are based on keyword matching, personalization, and social matching. Keyword search queries against an index in the Microsoft Graph, which maps to locations in documents or a set of documents. Microsoft 365 leverages the Microsoft Graph to prioritize relevant content based on understanding of additional signals for users and their close network. This is known as personalization and social matching in Microsoft 365, which drives relevance for queries against the content in your organization. Access to tenant data in Microsoft Graph is gated by role-based access control, and organizations are always in control of Microsoft Search capabilities via the Search and Intelligence portal in the Microsoft 365 admin center.

## How the semantic index helps manage your data

The semantic index builds upon keyword matching, personalization, and social matching capabilities within Microsoft 365 by creating vectorized indices to enable conceptual understanding, which helps determine your intent and helps you find what organizational content you need. A vector is a numerical representation of a word, image pixel or other data point and is arranged or mapped with close numbers placed in proximity to one another to represent similarity. Unlike a standard keyword index, vectors are stored multi-dimensional spaces where semantically similar data points are clustered together in the vector space, enabling Microsoft 365 to handle a broader set of search queries beyond “exact match.” The graphic below uses text (instead of numbers used by vectorized indices) to show an example of similarity between data points:

:::image type="content" source="media/semantic-index-vector-example.png" alt-text="Graphic showing an example of how data points for Semantic Index are clustered together.":::

This approach provides for fast and accurate similarity search and retrieval of data based on their vector distance or similarity. This means that instead of using traditional methods for querying based on exact matches or predefined criteria, the semantic index can find the most similar or relevant data based on the semantic or contextual meaning.

## Features

The following semantic index features do more than enhance search results; they work together to help you understand your data, find information quicker and improve productivity. Users will be able to interact with the semantic index initially through Microsoft 365 Chat integration, and then over time, Microsoft will improve the search experience in SharePoint Online, Microsoft Teams, and the Microsoft 365 app by adding semantic index features that produce the results shown below:

:::image type="content" source="media/semantic-index-microsoft-365-chat.png" alt-text="Graphic showing the relationship between Microsoft 365 Chat and Microsoft Search." lightbox="media/semantic-index-microsoft-365-chat.png":::

Microsoft 365 Copilot and Microsoft 365 E3, E5, Business Standard and Business Premium customers will receive the features as part of a phased rollout, with status updates shared via the [Microsoft 365 admin center](https://admin.microsoft.com/) and [Microsoft 365 public roadmap](https://www.microsoft.com/microsoft-365/roadmap). A breakdown of each feature when searching for information is included below.

### Microsoft 365 Chat

The Semantic index helps surface results within Microsoft 365 Chat (part of Microsoft 365 Copilot) by understanding the intent of your query and appending additional information to your Microsoft 365 Chat prompt. Relevant information is obtained in the Microsoft Graph and semantic index to provide the LLM with more information to reason over. For example, if you ask Microsoft 365 chat to find an email where a colleague was happy with the design work of a vendor, semantic index adds adjacent words (for example, elated, excited, amazed) into the search to widen the search area and provide the most relevant result. All of this work takes place behind the scenes to add relevance to results that you search for with Microsoft 365 chat, without added complexity.

### Semantic Search

Semantic Search captures the semantic meaning of your query, such that semantically similar text has similar numerical values to better understand the language. By using vectors, Semantic Search can understand relationships between different forms of words (for example, tech, technology, technologies; USA, U.S.A, United States, United States of America; dog, cat, pet), and naturally capture synonyms to expand the amount of information that can be searched for. These improvements help Semantic Search understand the intent of sentences, snippets, documents, meetings. It also identifies related assets to your query or sample content, and prepares users for interacting with Microsoft 365 Copilot.

## How the semantic index works

The semantic index enhances Microsoft 365 Chat and search results in the [Microsoft 365 app](https://www.microsoft365.com/), SharePoint Online, and Microsoft Teams. It does this by creating two indexes to support an enhanced search experience and conceptual understanding of your online data that are enabled automatically by Microsoft. 

User-level indexing creates a personalized index for your eyes only on a working set of data, and makes it more accessible for you to use with everyday tasks. Any text-based content that you create or interact with is included, such as emails, documents you're mentioned in, comment on, or share. The tenant-level index adds text-based SharePoint Online files that are accessible by two or more people in your organization via site inheritance. However, it only surfaces the results to a user if the user already has access to the content controlled by role-based access control. Additionally, the SharePoint Online site must remain searchable.

This section reviews how each index is enabled, how the semantic index interacts with the data flow in Microsoft 365 Copilot, what types of files are supported by the index, and how each index processes updates.

## Enablement

We are in the early stages of rolling out the semantic index to all organizations with Microsoft 365 Copilot and an eligible Microsoft 365 license, without any administrative involvement. Microsoft automatically manages the enablement of the semantic index, with prioritization given for organizations that purchase more than 300 licenses for Microsoft 365 Copilot. When user indexing is complete, administrators will see the ‘Semantic indexing is complete’ status in the Microsoft 365 admin center for enabled users. When tenant level indexing starts in an organization, admins will see ‘Semantic index is available for your organization’ on the Search and Intelligence page in the Microsoft 365 admin center.

:::image type="content" source="media/semantic-index-enabled.png" alt-text="Screenshot showing semantic index enabled.":::

> [!IMPORTANT]
> Microsoft will not provide timelines or status of semantic indexing of user and tenant level indexing for individual tenants. Organizations are advised to use the process above to check on indexing status for their tenants.

## Data flows

The semantic index interacts with the Microsoft Graph to provide users with access to information in the user level and tenant level index. The diagram below shows how the flow of data works for a request using Microsoft 365 Copilot.

:::image type="content" source="media/semantic-index-flow-chart.png" alt-text="Graphic showing the relationship between Microsoft 365 Copilot, Microsoft 365 Apps, Microsoft Graph, and Large Language Model." lightbox="media/semantic-index-flow-chart.png":::

User prompts from Microsoft 365 apps are sent to Copilot (1), and Copilot accesses the Microsoft Graph and semantic index for processing (2). Copilot sends the modified prompt to the Large Language Model (3), receives the LLM response (4), and then accesses the Microsoft Graph and semantic index for post-processing (5). Copilot then sends the response and app command back to Microsoft 365 apps. All requests are encrypted by HTTPS and customer data remains encrypted at rest.

## Supported content types

The semantic index will support indexing of user mailbox and file types listed in the following table, with more file types supported over time. A list of supported file types for the user level index and tenant level index at time of publish is included in the table. For the most recent set of supported file types visit the [semantic index documentation page](https://aka.ms/SemanticIndex):

| **Content/file type**     | **User level** | **Tenant level** |
|---------------------------|----------------|------------------|
| User Mailbox              | Supported      | Not applicable   |
| Delegated Mailbox         | Not supported  | Not applicable   |
| Shared Mailbox            | Not supported  | Not applicable   |
| Archived Mailbox Data     | Not supported  | Not applicable   |
| Archived SharePoint Data  | Not supported  | Supported\*      |
| Word documents (doc/docx) | Supported      | Supported        |
| PowerPoint (pptx)         | Supported      | Supported        |
| PDF files                 | Supported      | Supported        |
| Web pages (aspx)          | Supported      | Supported        |
| OneNote files (one)       | Supported      | Supported        |
| Graph Connector data      | Not applicable | Supported        |

\*Support for archived SharePoint Data extends only to the supported file types in this list. Support for more file types will be communicated in the Microsoft 365 Public Roadmap and documentation.

## Index updates

When the semantic index has completed indexing for a customer for the first time, documents created by users are indexed in near real-time in the user's mailbox. New documents that are added to SharePoint Online sites that are accessible, via site inheritance, by two or more users are indexed daily. When an indexed user and tenant level document is updated, the changes are immediately indexed.

## Administration

We provide administrators with optional activities to prepare and manage the semantic index via the Microsoft 365 admin center. There's no administrative involvement required to enable the semantic index, as the service is automatically enabled by Microsoft. The semantic index is an improvement to Microsoft 365 search and cannot be disabled. 

Administrators can choose to prepare and manage the semantic index by reviewing the considerations for [planning and deploying a file collaboration in SharePoint](/sharepoint/deploy-file-collaboration) and [sharing permissions in the SharePoint modern experience](/sharepoint/modern-experience-sharing-permissions). Administrators can then exclude SharePoint Online sites from the tenant level index, configure item insights from the Search Intelligence page in the Microsoft 365 admin center, or incorporate third party information into the semantic index.

## Excluding SharePoint Online Sites

There are times when organizations may wish to exclude a SharePoint Online site from having its data indexed by Microsoft Search and the semantic index tenant level index including sensitive data such as payroll, HR or financial information. To exclude a SharePoint Online site, follow these steps:

1. Browse to the site with appropriate administrator permissions.
1. Select **Settings** then **Site information** from the drop-down menu.
1. Select **View all site settings** to bring up the Site Settings page.
1. Select **Search and offline availability** under the **Search** category and select **No** for **Allow this site to appear in search results** to exclude it from both Microsoft Search and the semantic index search. This can also be performed with PowerShell for multiple sites.

:::image type="content" source="media/semantic-index-settings.png" alt-text="Screenshot showing the settings for excluding SharePoint online sites." lightbox="media/semantic-index-settings.png":::

Microsoft Search and the semantic index support the exclusion of SharePoint online content from the tenant level index only. There's no option to exclude results from Microsoft Search only or the semantic index only; actions apply to both at the same time.

## Configuring Item Insights

On the Search and Intelligence page in the Microsoft 365 admin center, Item insights are enabled by default. Turning off people or item insights reduces the Microsoft Search and semantic index experience as results won't include relevant people that would have been derived from distribution groups or from the organizational chart.

- **People insights** provide a list of relevant people to a user based on their public collaborative work in Microsoft 365. Public collaboration includes members of a public distribution group, individuals connected in the organizational chart.

- **Item insights** allow recommendations for people in your organization based on their collaborative work in Microsoft 365. These recommendations might include but aren't limited to documents or other types of content and show up in people cards (contacts), Delve, The [Microsoft 365 app](https://www.microsoft365.com/), Microsoft 365 chat results, and other locations.

Both Item insights and People Insights don't cover personalization features based on a user's own data.

## Incorporating third party information

The semantic index provides a way for organizations to bring your organizational data or content outside of Microsoft 365 into Microsoft 365 Copilot and the Microsoft 365 ecosystem. Graph connectors enable ingestion of external data sources, which help enrich users’ Copilot experience with relevant results that leverage first, as well as third party data. Microsoft indexes all your Graph connectors data while maintaining access controls for content. This expands the types of content sources that are searchable in your Microsoft 365 productivity apps and the broader Microsoft ecosystem, and works best when connector content is text rich. The third-party data can be hosted on-premises or in the public or private clouds, and this information is consumed by the Microsoft Graph, which can be ingested into the semantic index to help provide your organization with all the context across Microsoft 365 and your organization’s third party content. Learn more about graph connector licensing requirements for Microsoft 365 Enterprise and Microsoft 365 Copilot at [License requirements and pricing](licensing.md).

Additionally, more than 30 plugins and Graph connectors, including Web search powered by Bing, Microsoft Dataverse, Jira, Trello, Mural, Confluence, Freshworks, and Priority Matrix are now available. Thousands of additional line-of-business and third-party plugins will be enabled in the coming months as we integrate existing Teams message extensions and Microsoft Power Platform connectors with Microsoft 365 Copilot. This extensive ecosystem of plugins for Microsoft 365 Copilot surfaced in the tools used every day for work will bring unprecedented value to our mutual customers as we transform how work gets done together.

## Privacy, Compliance, and Security

The permissions model within your Microsoft 365 tenant can help ensure that data won't unintentionally leak between users, groups, and tenants. The semantic index presents only data that each individual can access using the same underlying controls for data access used in other Microsoft 365 services. Semantic index honors the user identity-based access boundary so that the grounding process only accesses content that the current user is authorized to access. For more information, see [Microsoft’s privacy policy and service documentation](https://privacy.microsoft.com/).

Microsoft 365 Copilot is compliant with our existing privacy, security, and compliance commitments to Microsoft 365 commercial customers, including the General Data Protection Regulation (GDPR) and European Union (EU) Data Boundary. Prompts, responses, and data accessed through the semantic index aren't used to train foundation LLMs, including those used by Microsoft 365 Copilot. For more information, see [Data, Privacy, and Security for Microsoft 365 Copilot](/microsoft-365-copilot/microsoft-365-copilot-privacy).

## Storage & Processing

Data generated by the semantic index remains within your company’s tenant, and complies with your security, compliance, identity, and privacy policies and processes. The semantic index works only with content to which your users already have permission and doesn't affect storage quotas.

User-level index information is stored where the user's mailbox is located, and the tenant-level index information is stored in an isolated and protected customer’s tenant container located in the region where the SharePoint site is located (Home region or otherwise specified by tenant admin). For customers within the European Union Data Boundary (EUDB), the index is stored in a EU/EFTA based datacenter. Processing other customers can take place either in a tenant region or in the United States. For multi-geo organizations, all geographical boundaries are respected. In-region data is stored and processed in each region. At query time, a federated query is sent to all regions and merges semantic index and keyword search results into one response to the user.

## Microsoft Purview Customer Key (BYOK) support

The semantic index provides BYOK support for enterprises that have enabled BYOK in their environment for both the user level index and the tenant level index. Microsoft automatically enables the semantic index for BYOK enabled customers without any administrative involvement.

## Information Protection

In the context of search, there are no additional ways to exclude data from the semantic index using information protection capabilities. The semantic index inherits security and privacy settings from Microsoft Search, and data brought in from third party connectors will be provided the same storage and protections as other Microsoft 365 data. For organizations that are investigating additional information protection options, Microsoft 365 provides built-in capabilities in Microsoft 365 apps and add-on products to help Administrators protect organizational data through data minimalization and reducing oversharing. The following sections outline the options available for organizations for reference only.

## Data minimalization

Data minimalization reduces the amount of data available to be accessed within your organization. Retaining and deleting content is often needed for compliance and regulatory requirements, but deleting content that no longer has business value also helps you manage risk and liability.[Microsoft Purview Data Lifecycle Management](/purview/data-lifecycle-management), which is [licensed separately](https://azure.microsoft.com/products/purview/), can be used to delete content that is no longer needed with retention policies for management at scale, and retention labels for exceptions and granular control.

## Reduce oversharing

Organizations have long been able to take action to reduce oversharing in Microsoft 365 using existing controls in the Microsoft 365 admin center and SharePoint Online. It's important to note that semantic index doesn't change access permissions to content and doesn't change the principles of how users should share information with colleagues. For example, the semantic index doesn't make content shared with a link that works with everyone in my organization part of the tenant level index. Only users that select a link that they have access to will have the information added to their user index. It's recommended that organizations consider the following when exploring information protection options:

- **Plan secure file collaboration** – Review [Plan and deploy a file collaboration](/sharepoint/deploy-file-collaboration) to understand more about recommended practices to operate a secure and productive file collaboration environment for your users.

- **Right size user access to data to reduce the list** – reduce oversharing by inheriting exclusion lists for SharePoint Online sites and performing access control checks in real time that is present in the semantic index. Organizations can consider using the [Syntex SharePoint Advanced Management add-on](/sharepoint/advanced-management) to manage and govern these permissions.

- **Use sensitivity labels** - Another way is to label the data with [Microsoft Purview Information Protection](/purview/information-protection) sensitivity labels, available with Microsoft 365 Business Premium and Microsoft 365 E3 and E5. Labels that apply encryption use usage rights to provide an extra layer of protection, and these are also included in search trimming (that is, supported for filtering and application side rules used for visual marking and access restrictions).

- **Limit access** – [Microsoft Purview Data Loss Prevention](/purview/dlp-learn-about-dlp) is available in Microsoft 365 E5 and could be used to retroactively and temporarily limit access to documents that have been reported as overshared. If you're not a Microsoft 365 E5 customer, organizations can use the 90-day Microsoft Purview solutions trial to explore how additional Purview capabilities can help your organization manage data security and compliance needs.

For customers interested in exploring how to deploy advanced information protection solutions, review the following article that explains how to [deploy an information protection solution with Microsoft Purview](/purview/information-protection-solution). For more information about how Microsoft Purview can help you strengthen your data security and compliance requirements for Microsoft 365 Copilot, see [Protect and manage Microsoft 365 Copilot interactions with Microsoft Purview](/purview/ai-microsoft-purview).

## Additional resources

Microsoft 365, the Microsoft Graph and the semantic index enable an unprecedented expressiveness for search, chat and copilots leveraging Microsoft 365 data. This expressiveness helps surface the right grounding data to get the most out of your organizational data with Microsoft 365 and Microsoft 365 Copilot.

To learn more about Microsoft 365 Copilot, check out these resources:

- [Get started with Copilot in Microsoft 365](/microsoft-365-copilot/microsoft-365-copilot-setup)
- [Data, Privacy, and Security for Microsoft 365 Copilot](/microsoft-365-copilot/microsoft-365-copilot-privacy)
- [Microsoft 365 Copilot adoption site](https://adoption.microsoft.com/copilot/)
