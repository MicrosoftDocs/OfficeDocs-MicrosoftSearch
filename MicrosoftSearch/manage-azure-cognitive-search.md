---
title: "Azure Cognitive Search results in Microsoft Search (Preview)"
ms.author: kellis
author: kellis
manager: kellis
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
ms.date: 03/27/2023

description: "Manage how Azure Cognitive Search content appears in search results"
---
# Azure Cognitive Search results in Microsoft Search (Preview)

[Azure Cognitive Search](/azure/search/search-what-is-azure-search) is a cloud search service that gives developers infrastructure, APIs, and tools for building a rich search experience over private, heterogeneous content. With this connector, users can search for their Azure Cognitive Search (ACS) data directly from their Microsoft Search endpoints. The connection has some key benefits:

* **Easy to use:** Users can easily and quickly find key information stored in Azure Cognitive Search (ACS), without needing to navigate to a new app or page.
* **Easy to find:** ACS content is visible to users in Bing.com, Office.com, and SharePoint.
* **Customizable permissions:** ACS results can be configured to appear for everyone in the organization or refined to certain people using Azure Role-Based Access Control.
* **Adaptable result layouts:** ACS results can be formatted with a default layout, based on your data’s schema, or can be customized using Modern Result Types.
* **Quick setup:** Simple to configure and easy to maintain the search connection to an ACS index.
* **Unified search experience:** To maintain a cohesive experience, ACS results are consistent across all search entry points. Wherever you search, you get the same results with the same look and feel.

Our Azure Cognitive Search connector is currently in preview. If you're interested in joining the preview, let us know at [aka.ms/D365-ACS-Preview-MicrosoftSearch](https://aka.ms/D365-ACS-Preview-MicrosoftSearch).

## What users experience

ACS results appear in a dedicated vertical, or tab, in the search experience. For example, the ACS results that appear on a Bing work results page are the same that appear on an Office.com or SharePoint results page.

:::image type="content" alt-text="Results from Azure Cognitive Search in Bing work results" source="media/azure-cognitive-search/acs-results-bing.png" lightbox="media/azure-cognitive-search/acs-results-bing.png":::

:::image type="content" alt-text="Results from Azure Cognitive Search in Office.com results." source="media/azure-cognitive-search/acs-results-office.png" lightbox="media/azure-cognitive-search/acs-results-office.png":::

Check out our Microsoft Build 2022 video for a demonstration.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Ybrw]


## Prerequisites

* To connect Azure Cognitive Search with Microsoft Search, you first need to create an ACS service with at least one index. Follow the instructions here to get set up: [Create a Search Service](/azure/search/search-create-service-portal).
* The search administrator configuring the connection with Microsoft Search must have Search Administrator permissions to set up the connection in the Microsoft Admin Center.
* If you plan to connect to your ACS service using Role-Based Access Control, the Search Administrator configuring the connection in the Microsoft Admin Center must have either the **Search Index Contributor** role assigned, or both **Contributor** and **Search Index Data Reader** roles for your ACS service. See instructions here on how to assign roles here: [Assign roles](/azure/search/search-security-rbac?tabs=config-svc-portal%2Croles-portal%2Ctest-portal%2Ccustom-role-portal%2Cdisable-keys-portal#assign-roles).

## Setup

1. Grant Reader permissions for the Bing app in the Azure portal - this gives us permission to view the Azure Cognitive Search resource from Microsoft Search in Bing:

    * Navigate to the [Azure portal](https://portal.azure.com) and open your Azure Cognitive Search resource.
    * Select **Access control (IAM) on the left sidebar**, then navigate to the **Role assignments** tab.
    * Select **Add** in the top left corner, then **Add role assignment** from the dropdown.
    * Choose the **Reader** role from the list, and click **Next**.
    * On the following page, click on **Select members**, then in the search box, which opens to the right, search for **Bing**.
    * Select **Bing** in the search results, and hit **Select**.
    * Select **Review + assign**, then **Review + assign** again.

2. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to [Data sources](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/connectors). In the Microsoft apps and services section, select **Add a new app or service**. :::image type="content" alt-text="Data sources page with link to Add new app or service highlighted." source="media/azure-cognitive-search/acs-data-source.png" lightbox="media/azure-cognitive-search/acs-data-source.png":::
3. Select **Azure Cognitive Search**, then **Next**.
4. In the **Connection details** pane, enter the connection name and description. The name is used as the display name for the ACS vertical on Bing, Office.com, and SharePoint.
5. In the Data source field, enter the URL for your ACS index, using the format `<your-service>.search.windows.net/indexes/<your-index>`. Replace `<your-service>` with the name of the search service resource, and `<your-index>` with the name of the index.
6. In the Azure resource ID field, add the Resource ID for your ACS index. It can be found in the Azure portal with the following steps:
    * Open your ACS resource in the [Azure portal](https://portal.azure.com)
    * Select the **Properties** tab, and copy the ID under the **Essentials** heading
7. Choose whether you want to connect to your ACS index using API key authentication or Azure Role-Based Access Control (RBAC). **Note:** if you select API Keys, the connected ACS index will be searchable by all Microsoft Search users in your organization. In order to limit permissions to a subset of users, configure Azure RBAC for your ACS index, and select Azure Role-Based Access Control here. For more information on Role-Based Access control, see: [RBAC Search Security](/azure/search/search-security-rbac).
    * If you selected API Key authentication, enter your Admin API key and, optionally, a Query API key. The Admin API key is used to fetch the data schema and the Query key is used at query time. For information about finding or creating API keys, see [Find existing keys](/azure/search/search-security-api-keys#find-existing-keys).
8. Choose whether you want queries on your ACS content to use Semantic Search or Simple Search. If you want to use Semantic Search, you'll need to have it enabled for your ACS service. These queries will use your ACS semantic query quota and could incur extra costs through Azure Billing. For more information on Semantic Search, see [Semantic Search Overview](/azure/search/semantic-search-overview).
9. Read and select the authorization check boxes, then test your setup with the **Test connection** button. Fix any errors, then select **Next**.
10. In the **Add semantic property labels** pane:
    * If these labels are sufficient to display the results, select the source properties you’d like to display for each of the listed labels. The selected properties are used to create a default Modern Result Type (MRT) for the results. You must select a property for the Title. The others are optional but recommended, since they make the results more informative.
    * If these labels aren't adequate to display your results, you can leave them blank and create a custom MRT later. For information about creating a custom MRT, see [Manage result types](/microsoftsearch/manage-result-types).
11. Verify the information entered is correct and select **Finish**.
12. When the connection has been created, you'll be redirected to the Data Sources page again. You should see your newly created connection with the status **Ready**. :::image type="content" alt-text="Azure Cognitive Search connection successfully created." source="media/azure-cognitive-search/acs-custom-vertical.png" lightbox="media/azure-cognitive-search/acs-custom-vertical.png":::
13. You can create up to three ACS connections per tenant - repeat the above steps for other connections you want to create.

> [!TIP]
> To clarify the type of content users can find in the search vertical, we recommend updating the vertical name. To customize the name of your vertical, navigate to the **Customizations** tab, select **Verticals** in the left sidebar and choose your newly created vertical. For more information, see [Manage search verticals](/microsoftsearch/manage-verticals).

> [!NOTE]
> After the connection is enabled, it may take up to 24 hours for your new vertical and ACS results to appear in your Microsoft Search endpoints because of caching at various layers of the system.

## Query patterns

Two forms of query syntax are supported for ACS results in Microsoft Search: simple search and semantic search. You can select the query mode for your connection during setup.

Simple Query Syntax includes Keyword Query Language, AND, OR, and NOT operators. For more information, see [Simple query syntax in Azure Cognitive Search](/azure/search/query-simple-syntax). To adjust which data fields are searchable, you can [modify the field attributes for your ACS index](/azure/search/search-what-is-an-index#field-attributes).

Semantic search uses semantic ranking to find context and relatedness among terms, and language understanding to create summarizations within your content. For more information, see [Semantic Search Overview](/azure/search/semantic-search-overview).

## Customize result types

To alter the way your ACS results are formatted, for example, layout or the fields displayed, you can create a custom Modern Result Type. To get started, go to [Result Types settings](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/resulttypes) in the Microsoft 365 admin center. For more information, see [Manage result types](/microsoftsearch/manage-result-types).

## Edit the connection

After enabling the connection, you can modify the endpoint and connection name. In [Data sources](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/connectors), select the configured connection to make changes.  :::image type="content" alt-text="Azure Cognitive Search connection and pane with connection details." source="media/azure-cognitive-search/acs-edit-settings.png" lightbox="media/azure-cognitive-search/acs-edit-settings.png":::

To deactivate the connection, clear the **Activate this connection for your organization** check box and **Save**.

## Troubleshooting

* **I'm getting a setup error but all the values I entered are correct!** Ensure that you've completed all the prerequisites listed above the setup instructions.

* **I have a private ACS endpoint, can I use this integration?** At this time, we don't support connecting to private ACS endpoints. 

* **The ACS index I want to connect is part of a different Microsoft 365 tenant, can I still connect it in Microsoft Search?** At this time, we don't support cross-tenant connection. The ACS service must be part of the same Microsoft 365 tenant in which you want to make the content available in Microsoft Search.

* **End users aren't seeing any results, why?** There are a few reasons why your end users may not be seeing ACS content in Microsoft Search, verify the following:

    * You've waited more than 24 hours after configuring the connection before checking for results in Microsoft Search endpoints.
    * If you set up the connection to Microsoft Search using the Role-Based Access Control Authorization option, make sure that you have assigned the desired users or groups Search Index Data Reader permissions through the Azure portal.
    * Check that the authorization settings for your ACS service match the settings in your Microsoft Admin Center. For example, if API key authentication is selected in the Microsoft Admin Center, ensure that this is still the correct setting for your search service in the Azure portal.

If you have feedback or questions when using the preview connector, [contact us](https://aka.ms/ACSConnectorFeedback).
