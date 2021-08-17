---
title: "Dynamics 365 federation search (preview)"
ms.author: dawholl
author: dawholl
manager: kellis
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal

description: "Manage how Dynamics 365 content appears in search results"
---
# Dynamics 365 federation search (preview)

## Microsoft Search Federation and connectors

To help make Microsoft Search more useful, we're introducing Microsoft Search Federation. With federated search, organizations can make data in these scenarios accessible in Microsoft Search:

* Data in systems that are subject to strict compliance requirements
* Data that can't leave system boundaries
* Sensitive data stored on-prem that your organization doesn’t want indexed on the cloud

Data accessed through a federated search connection isn't indexed in Microsoft Search. Also, using built-in connectors from Microsoft, it's easy to set up federated search connections. Our Dynamics 365 connector is currently in preview. If you're interested in joining the preview, let us know at [aka.ms/D365FederationSearchPreview](https://aka.ms/D365FederationSearchPreview). For current status and release time frames, see the [Microsoft Search Roadmap](https://www.microsoft.com/microsoft-365/roadmap?filters=Microsoft%20Search).

## Dynamics 365 federation connector

Microsoft Dynamics 365 is a line of intelligent business applications designed for enterprise resource planning and customer relationship management. With Dynamics 365 federation, Microsoft Search provides a seamless search experience, enabling users to easily find the most relevant customer and business data stored in Dynamics 365. The Dynamics 365 federation connector provides some key benefits:

* **Easy to administer:** Streamlined process to configure and maintain the search connection to a Dynamics 365 instance.
* **Easy to use:** Users can easily and quickly find key information stored in Dynamics 365, including accounts, contacts, open opportunities, and more.
* **Richer content:** To make Dynamics 365 search results more useful, they include key information like leads, contacts, and account details.
* **Built-in data protection:** Dynamics 365 results will only appear for users that have access to the connected instance.
* **Unified search experience:** To maintain a cohesive experience, Dynamics 365 results are consistent across all search entry points. Wherever you search, you'll get the same results with the same look and feel.

## What users experience

Dynamics 365 answers appear in search results across all Microsoft Search canvases, including SharePoint Online, Bing, and Office.

:::image type="content" alt-text="Screenshot of Dynamics 365 answers on SharePoint, Bing, and Office" source="media/dynamics365/dynamics365-answer.png" lightbox="media/dynamics365/dynamics365-answer.png":::

From the answer, it's easy to see more Dynamics 365 search results by using the **More Dynamics 365 results** link. It takes users to a dedicated Dynamics 365 results page with more results relevant to their query.

:::image type="content" alt-text="Screenshot of Dynamics 365 vertical and results on SharePoint, Bing, and Office" source="media/dynamics365/dynamics365-vertical.png" lightbox="media/dynamics365/dynamics365-vertical.png":::

Clicking or tapping any result opens Dynamics 365 and shows the detailed information.

:::image type="content" alt-text="Screenshot of detail page in Dynamics 365" source="media/dynamics365/dynamics365-detail-page.png" lightbox="media/dynamics365/dynamics365-detail-page.png":::

No matter where your users start their search their experience will be consistent and enable them to quickly find the most relevant Dynamics 365 results. Check out our Microsoft Build 2021 video for a demonstration.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4P83t]

## Supported query patterns

Both natural language and product name queries are supported when using Microsoft Search to find Dynamics 365 results. Also, Dynamics 365 queries aren't case sensitive. Use natural language patterns to find contact, account, and opportunities--by customer name or location--and other frequently used queries. Here are a few examples:

* Who is the contact for Contoso
* Open opportunities for Contoso
* What are open opportunities in Seattle
* What are the accounts in Seattle
* What are the contacts in Seattle
* What are my leads closing this month
* High priority phone call
* Contact missing emails

Product name patterns support a range of Dynamics 365 applications and will trigger Dynamics 365 results regardless of where they appear in a query:

* D365
* Dynamics 365
* Dynamics365
* Dynamics CRM
* Dynamics Sales
* Dynamics Customer Service
* Dynamics Service
* Dynamics Field Service

## Configure the Dynamics 365 connector

With this simple configuration, you can enable the Dynamics 365 federation search experience for people in your organization.

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to [Data sources](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/connectors).

2. In the Microsoft apps and services section, under Microsoft Dynamics 365, select **Manage** to open the Microsoft Dynamics 365 panel.

3. Enable the connector for your organization.

4. In the **Endpoints** list, select your Dynamics 365 environment.

5. In the **Connection ID**, enter a unique ID for this connection.

6. Review and select the consent check box.

7. Select **Save** to finish the connection setup.

:::image type="content" alt-text="Screenshot of Dynamics 365 set-up panel in the Microsoft 365 admin center" source="media/dynamics365/dynamic365-connection-setup.png" lightbox="media/dynamics365/dynamic365-connection-setup.png":::

When the setup is complete, Dynamics 365 answers and vertical will only appear for users with a valid Dynamics 365 license and access to the connected Dynamics 365 environment. At any time, you can return to these settings and change the connection endpoint environment or deactivate the connection.
