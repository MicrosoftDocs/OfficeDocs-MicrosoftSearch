---
title: "Azure Cognitive Search results in Microsoft Search (Preview)"
ms.author: dawholl
author: dawholl
manager: kellis
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
ms.date: 06/03/2022

description: "Manage how Azure Cognitive Search content appears in search results"
---
# Azure Cognitive Search results in Microsoft Search (Preview)

[Azure Cognitive Search](/azure/search/search-what-is-azure-search) is a cloud search service that gives developers infrastructure, APIs, and tools for building a rich search experience over private, heterogeneous content in web, mobile, and enterprise applications. With this connector, users can search for their Azure Cognitive Search (ACS) data directly from their Microsoft Search endpoints. The connection has some key benefits:

* **Easy to use:** Users can easily and quickly find key information stored in Azure Cognitive Search (ACS), without needing to navigate to a new app or page.
* **Easy to find:** ACS content is visible to users in Bing.com, Office.com, and SharePoint.
* **Customizable permissions:** ACS results can be configured to appear for everyone in the organization or specific Azure AD access control lists.
* **Adaptable result layouts:** ACS results can be formatted with a default layout, based on your data’s schema, or can be customized using Modern Result Types.
* **Quick setup:** Simple to configure and easy to maintain the search connection to an ACS index.
* **Unified search experience:** To maintain a cohesive experience, ACS results are consistent across all search entry points. Wherever you search, you'll get the same results with the same look and feel.

Our Azure Cognitive Search connector is currently in preview. If you're interested in joining the preview, let us know at [aka.ms/D365-ACS-Preview-MicrosoftSearch](https://aka.ms/D365-ACS-Preview-MicrosoftSearch).

## What users experience

ACS results will appear in a dedicated vertical, or tab, in the search experience. For example, the ACS results that appear on a Bing work results page are the same that appear on an Office.com or SharePoint results page.

:::image type="content" alt-text="Results from Azure Cognitive Search in Bing work results" source="media/azure-cognitive-search/acs-results-bing.png" lightbox="media/azure-cognitive-search/acs-results-bing.png":::

:::image type="content" alt-text="Results from Azure Cognitive Search in Office.com results." source="media/azure-cognitive-search/acs-results-office.png" lightbox="media/azure-cognitive-search/acs-results-office.png":::

Check out our Microsoft Build 2022 video for a demonstration.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Ybrw]

## Setup

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to [Data sources](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/connectors).
2. In the Microsoft apps and services section, select **Add a new app or service**. :::image type="content" alt-text="Data sources page with link to Add new app or service highlighted." source="media/azure-cognitive-search/acs-data-source.png" lightbox="media/azure-cognitive-search/acs-data-source.png":::
3. Select **Azure Cognitive Search**, then **Next**.
4. In the **Connection details** pane:

    - Enter the connection name and description. The name will be used as the display name for the ACS vertical on Bing, Office.com, and SharePoint.
    - In the Data source field, enter the URL for your ACS index, using the format `<your-service>.search.windows.net/indexes/<your-index>`. Replace `<your-service>` with the name of the search service resource, and `<your-index>` with the name of the index.
    - Add your Admin and Query API keys. For information about finding or creating API keys, see [Find existing keys](/azure/search/search-security-api-keys#find-existing-keys).
    - Select the authorization check box, then **Next**.

5. On the **Search permissions** page, choose to enable the connection for everyone in your organization or restrict the results to certain Access Control Lists.
6. In the **Add semantic property labels** pane:

    - If these labels are sufficient to display the results, select the source properties you’d like to display for each of the listed labels. The selected properties will be used to create a default Modern Result Type (MRT) for the results. You must select a property for the Title. The others are optional but recommended, since they make the results more informative.
    - If these labels aren't adequate to display your results, you can leave them blank and create a custom MRT later. For information about creating a custom MRT, see [Manage result types](/microsoftsearch/manage-result-types).

7. Verify the information entered is correct and select **Finish**.
1. When the connection has been created, you'll be redirected to the Data Sources page again. If you want to change the display name that appears on the ACS vertical, select **Edit vertical** below the newly created ACS connection. :::image type="content" alt-text="Azure Cognitive Search connection with link to Edit vertical name." source="media/azure-cognitive-search/acs-custom-vertical.png" lightbox="media/azure-cognitive-search/acs-custom-vertical.png":::

For more information about verticals, see [Manage search verticals](/microsoftsearch/manage-verticals). After successfully configuring an ACS connection, you should see the connection state Ready.

> [!NOTE]
> After the connection is enabled, it may take up to 24 hours for your new vertical and ACS results to appear in your Microsoft Search endpoints because of caching at various layers of the system.

## Query patterns

Searching ACS results in Microsoft Search supports simple query syntax. This includes Keyword Query Language, AND, OR, and NOT operators. For more information, see [Simple query syntax in Azure Cognitive Search](/azure/search/query-simple-syntax). To adjust which data fields are searchable, you can [modify the field attributes for your ACS index](/azure/search/search-what-is-an-index#field-attributes).

## Customize result types

To alter the way your ACS results are formatted, for example, layout or the fields displayed, you can create a custom Modern Result Type. To get started, go to [Result Types settings](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/resulttypes) in the Microsoft 365 admin center. For more information, see [Manage result types](/microsoftsearch/manage-result-types).

## Edit the connection

After enabling the connection, you can modify the endpoint and connection name. In [Data sources](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/connectors), below the configured connection, select Edit to make changes.  :::image type="content" alt-text="Azure Cognitive Search connection and pane with connection details." source="media/azure-cognitive-search/acs-edit-settings.png" lightbox="media/azure-cognitive-search/acs-edit-settings.png":::

To deactivate the connection, clear the **Activate this connection for your organization** check box and **Save**.

## Troubleshooting

If any of the fields in your Modern Result Type for a particular result are blank, the field name will appear in curly braces.

:::image type="content" alt-text="ACS vertical with example fields 1 and 2 in curly braces." source="media/azure-cognitive-search/acs-result-troubleshooting.png" lightbox="media/azure-cognitive-search/acs-result-troubleshooting.png":::

To mitigate this issue, create a custom MRT and add this line: `"$when": "${exampleFieldName != null && exampleFieldName != ''}"` and replace `exampleFieldName` with the proper field name. Do this for any of the fields in the MRT that can be empty.

If you have feedback or questions when using the preview connector, [contact us](https://aka.ms/ACSConnectorFeedback).
