---
title: "Graph connectors SDK publish"
ms.author: rchanda
author: rchanda
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
description: "Graph connectors SDK publish"
---

# Publish your custom connector on M365 Admin Center

1. [Add a Microsoft Graph connector in the Microsoft 365 admin center](/microsoftsearch/configure-connector#step-1-add-a-microsoft-graph-connector-in-the-microsoft-365-admin-center)

2. Choose "Custom Connector" option and provide manifest details in the format below:

    ```json
    {
      // This is the unique connector id/provider id
      "connectorId": "<ConnectorGuid>",
    
      // This is list of all supported auth types. Remove the ones that the connector does not support.
      "authTypes": [ "Windows, Basic, Anonymous, OAuth2ClientCredentials" ],
      
      // The list of additional crawl types that the connector supports in addition to full and periodic full crawl. This is an optional field.
      "additionalCrawlsSupported": [ "Incremental" ]
    }

    ```

    a. connectorId should be a GUID. This is the same as ConnectorUniqueId in the Connector Info Service implementation file or the GUID defined by you.

    b. AuthTypes must be a non-empty array with one or more of Anonymous/Basic/Windows/OAuth type.

    c. Defining crawl types in addition to full and period full crawl is optional depending on the implementation and data source support.

    >[!Note]
    > The manifest file is generated automatically in the output directory of your project if you're using the C# project template. You may edit/update the manifest file as required.

3. [Name the connection](/microsoftsearch/configure-connector#step-2-name-the-connection)

4. Provide the URL to the data source you're connecting to and credentials to access it. Choose the Graph connector Agent available, and validate the information provided. Click Next on success.

5. Provide any additional configuration if required by your connector. You can pass any information specific to the connection to the datasource. For example, if you are building a connector for Azure DevOps, the projects which need to be indexed can be the additional parameters. For a Wiki connector, the sub-sections which need to be indexed can be the additional parameters. The API to query the wiki can take these filters specified in the additional parameters and get the items from datasource.

    The data in the parameter is opaque to the platform. It is serialized and stored as a string and passed to the connector. The connector can deserialize this as required and use it.

6. [Assign property labels](/microsoftsearch/configure-connector#step-6-assign-property-labels)

7. [Manage Schema](/microsoftsearch/configure-connector#step-7-manage-schema)

8. [Manage Search permissions](/microsoftsearch/configure-connector#step-5-manage-search-permissions) Only AAD based access control lists are supported for only people with access to the data source.

9. Select [refresh frequencies](/microsoftsearch/configure-connector#step-8-refresh-settings) of crawls

10. [Review](/microsoftsearch/configure-connector#step-9-review-connection) the details provided and click Finish

11. [Customize the search results page](/microsoftsearch/configure-connector#step-10-customize-the-search-results-page)

12. [Confirm if the connection setup worked](/microsoftsearch/configure-connector#step-11-confirm-if-the-connection-setup-worked)
