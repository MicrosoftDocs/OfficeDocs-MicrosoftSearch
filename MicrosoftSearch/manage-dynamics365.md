---
title: "Dynamics 365 results in Microsoft Search (Preview)"
ms.author: dawholl
author: dawholl
manager: kellis
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium

description: "Manage how Dynamics 365 content appears in search results"
---
# Dynamics 365 results in Microsoft Search (Preview)

Microsoft Dynamics 365 is a line of intelligent business applications designed for enterprise resource planning and customer relationship management. With Dynamics 365 results in Microsoft Search, users are able to easily find the most relevant customer and business data stored in Dynamics 365, right from Microsoft Search endpoints like Bing.com, Office.com, and SharePoint.com (and soon the Windows Search Box). The Dynamics 365 connector provides some key benefits:

*	**Easy to use:** Users can easily and quickly find key information stored in Dynamics 365, without needing to navigate to a new app or page.
* **Easy to find:** Dynamics 365 content is visible to users in Bing.com, Office.com and SharePoint.
* **Built-in data protection:** Dynamics 365 results will only appear for users that have access to the connected instance. 
* **Quick setup:** Quick setup to configure and easy to maintain the search connection to a Dynamics 365 instance.
* **Unified search experience:** To maintain a cohesive experience, Dynamics 365 results are consistent across all search entry points. Wherever you search, you'll get the same results with the same look and feel.


Our Dynamics 365 connector is currently in preview. If you're interested in joining the preview, let us know at [aka.ms/D365-ACS-Preview-MicrosoftSearch](https://aka.ms/D365-ACS-Preview-MicrosoftSearch).

## What users experience

Dynamics 365 answers appear in search results across all Microsoft Search canvases, including SharePoint Online, Bing, and Office.

:::image type="content" alt-text="Screenshot of Dynamics 365 answers on SharePoint, Bing, and Office." source="media/dynamics365/dynamics365-answer.png" lightbox="media/dynamics365/dynamics365-answer.png":::

From the answer, it's easy to see more Dynamics 365 search results by using the **More Dynamics 365 results** link. It takes users to a dedicated Dynamics 365 results page with more results relevant to their query.

:::image type="content" alt-text="Screenshot of Dynamics 365 vertical and results on SharePoint, Bing, and Office." source="media/dynamics365/dynamics365-vertical.png" lightbox="media/dynamics365/dynamics365-vertical.png":::

Clicking or tapping any result opens Dynamics 365 and shows the detailed information.

:::image type="content" alt-text="Screenshot of detail page in Dynamics 365." source="media/dynamics365/dynamics365-detail-page.png" lightbox="media/dynamics365/dynamics365-detail-page.png":::

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
* Dynamics Service
* Dynamics Field Service
* Dynamics Customer Service
* Dynamics Marketing
* Dynamics CE
* Dynamics Customer Engagement
* Customer Engagement

## Configure the Dynamics 365 connector

With this simple configuration, you can enable Dynamics 365 results in Microsoft Search for people in your organization. To successfully set up this connection, we recommend you confirm these settings before you begin:

* Dataverse search is enabled for the Dynamics 365 environment you want to connect to. For details, see [Configure Dataverse search for your environment](/power-platform/admin/configure-relevance-search-organization).
* The Search admin configuring the connector has administrator access to the Dynamics 365 environment. For more information, see [Assign licenses](/power-platform/admin/assign-licenses).

After verifying these settings, follow these steps to set up the connector:

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to [Data sources](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/connectors).

2. In the Microsoft apps and services section, under Microsoft Dynamics 365, select **Manage** to open the Microsoft Dynamics 365 panel.

3. Activate the connector for your organization.

4. In the **Endpoints** list, select your Dynamics 365 environment.

5. In **Connection Name**, enter a descriptive name for this connection.

6. Review and select the consent check box.

7. Select **Save** to finish the connection setup.

:::image type="content" alt-text="Screenshot of Dynamics 365 setup panel in the Microsoft 365 admin center." source="media/dynamics365/dynamic365-connection-setup.png" lightbox="media/dynamics365/dynamic365-connection-setup.png":::

> [!TIP]
> To clarify the type of content users can find in the search vertical, we recommend updating the vertical name. To customize the name of your Dynamics 365 vertical, click **Edit vertical**. For more information, see [Manage search verticals](/microsoftsearch/manage-verticals).

When the setup is complete, Dynamics 365 answers and vertical will only appear for users with a valid Dynamics 365 license and access to the connected Dynamics 365 environment. At any time, you can change the connection endpoint environment or deactivate the connection.
