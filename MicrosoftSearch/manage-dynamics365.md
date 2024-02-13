---
title: "Dataverse and Dynamics 365 results in Microsoft Search"
ms.author: davidedwards
author: dawholl
manager: kellis
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
ms.date: 05/03/2022

description: "Manage how Dataverse and Dynamics 365 content appears in search results"
---
# Dataverse and Dynamics 365 results in Microsoft Search

Microsoft Dataverse is a cloud storage platform that lets you securely store and manage data used by your business applications. Microsoft Dynamics 365 is a line of intelligent business applications built on the Dataverse Search platform, designed for enterprise resource planning and customer relationship management. With Dataverse results in Microsoft Search, users of both classic Dynamics 365 applications and custom model-driven Power Apps built on Dataverse are able to easily find their relevant customer data. The Dataverse connector provides some key benefits:

* **Easy to use:** Users can easily and quickly find key information stored in Dataverse and Dynamics 365, without needing to navigate to a new app or page.
* **Easy to find:** Dataverse and Dynamics 365 content is visible to users in Bing.com, Office.com, and SharePoint.
* **Built-in data protection:** Dataverse and Dynamics 365 results will only appear for users that have access to the connected instance and records. 
* **Quick setup:** Easy to configure and maintain the search connection to a Dataverse instance.
* **Unified search experience:** To maintain a cohesive experience, Dataverse results are consistent across all search entry points. Wherever you search, you'll get the same results with the same look and feel.

## User experience

Dataverse answers appear in search results across all Microsoft Search canvases, including SharePoint Online, Bing, and Office.

:::image type="content" alt-text="Screenshot of Dynamics 365 answers on SharePoint, Bing, and Office." source="media/dynamics365/dynamics365-answer.png" lightbox="media/dynamics365/dynamics365-answer.png":::

From the answer, it's easy to see more Dynamics 365 search results by using the **More Dynamics 365 results** link. It takes users to a dedicated Dynamics 365 results page with more results relevant to their query.

:::image type="content" alt-text="Screenshot of Dynamics 365 vertical and results on SharePoint, Bing, and Office." source="media/dynamics365/dynamics365-vertical.png" lightbox="media/dynamics365/dynamics365-vertical.png":::

Clicking or tapping any result opens Dynamics 365 or your custom application and shows the detailed information.

:::image type="content" alt-text="Screenshot of detail page in Dynamics 365." source="media/dynamics365/dynamics365-detail-page.png" lightbox="media/dynamics365/dynamics365-detail-page.png":::

No matter where your users start their search their experience will be consistent and enable them to quickly find the most relevant Dataverse results. Check out our Microsoft Build 2022 video for a demonstration.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Zf9u]

### Supported query patterns

Users will see results on the dedicated Dataverse and All verticals. Searches on either vertical aren't case sensitive.

On the dedicated vertical, search supports the same language used in Dataverse Search and classic Dynamics 365 applications, including simple operators like AND, OR, and NOT. For more information, see [Working with operators](/power-apps/user/relevance-search#working-with-operators).

On the All vertical, when there's a high confidence the user is searching for Dynamics results, the Dynamics answer is triggered. Natural language queries (queries that include common entities by name or location, for example) and queries that include the name of a Dynamics app can trigger an answer. Here are a few examples:

* Who is the contact for Contoso
* What are the accounts in Seattle
* High priority phone call
* Contact missing emails
* D365 contacts
* Contoso Dynamics Sales

## Admin experience

The Dataverse connector is easy to configure, customize, and edit. If you have feedback or questions when using the connector [contact us](https://aka.ms/Dynamics365ConnectorFeedback).

### Configure

With this simple configuration, you can enable Dataverse results in Microsoft Search for people in your organization. To successfully set up this connection, we recommend you confirm these settings before you begin:

* Dataverse search is enabled for the Dynamics 365 environment you want to connect to. For details, see [Configure Dataverse search for your environment](/power-platform/admin/configure-relevance-search-organization).
* The Search admin configuring the connector has the correct licenses to use Dynamics 365. For more information, see [Assign licenses](/power-platform/admin/assign-licenses).
* The Search admin has administrator access to the Dynamics 365 or Dataverse environment that you want to configure. For more information, see [Add users to environment](/power-platform/admin/add-users-to-environment).

After verifying these settings, follow these steps to set up the connector:

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to [Data sources](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/connectors).

2. In the Microsoft apps and services section, select **Add a new app or service**, then **Connect to Dynamics 365**. Select **Next** to open the connection details pane.

3. Enter a connection name and description. In the **Dynamics 365 environment** dropdown list, select the environment you want to connect to.

4. Review and select the consent check box. Select **Next** and review the connection details.

5. Select **Finish**, then **Done** to complete the connection setup.

6. After a successful setup, your Dynamics 365 connection should show a Connection state of Ready.

:::image type="content" alt-text="Screenshot of a Dynamics 365 connection successfully set up and showing a Ready connection state in the Microsoft 365 admin center." source="media/dynamics365/dynamic365-connection-setup.png" lightbox="media/dynamics365/dynamic365-connection-setup.png":::

> [!TIP]
> To clarify the type of content users can find in the search vertical, we recommend updating the vertical name. To customize the name of your vertical, click **Edit vertical**. For more information, see [Manage search verticals](/microsoftsearch/manage-verticals).

When the setup is complete, the dedicated Dataverse vertical and answers may take up to 24 hours to appear. Results will only appear for users with a valid Dynamics 365 license and access to the connected Dataverse environment. At any time, you can change the connection endpoint environment or deactivate the connection.

### Customize

Through Dataverse Search Quick Find Views, you can modify which entities and fields are searchable. The first four View Columns set in your Quick Find Views for each entity type will be displayed in your Microsoft Search results. Changes made to Quick Find Views will appear in Microsoft Search results and your Dynamics 365 apps. For information about modifying Quick Find Views, see [Select searchable fields and filters for each table](/power-platform/admin/configure-relevance-search-organization#select-searchable-fields-and-filters-for-each-table).

### Edit

After enabling the connection, you can modify the connection details, including the name, description, and environment. In [Data sources](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/connectors), below the configured connection, select **Edit** to make changes.
:::image type="content" alt-text="Screenshot of Dynamics 365 connector Edit button and panel in the Microsoft 365 admin center." source="media/dynamics365/dynamics365-edit-connector.png" lightbox="media/dynamics365/dynamics365-edit-connector.png":::

To deactivate the connection, clear the **Activate this connection for your organization** check box and **Save**.
