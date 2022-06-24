---
title: "Graph connectors SDK Contract Services"
ms.author: rchanda
author: rchanda
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
description: "Graph connectors SDK Contract Services"
---

# Services

The contract protocol buffer files have the following services which connector developer needs to implement:

|Services |Description |
|:----------|:-------------|
|[ConnectorInfo](/microsoftsearch/custom-connector-sdk-contracts-connectorinfo.md) |Service containing APIs to get information about the connector. If you're using our visual studio extension, this service has a default implementation and you don't have to make any change. |
|[ConnectionManagement](/MicrosoftSearch/custom-connector-sdk-contracts-connectionmanagement.md) |Service containing APIs that are called during the process of custom connector connection creation on Microsoft 365 admin center. |
|[ConnectorCrawl](/MicrosoftSearch/custom-connector-sdk-contracts-connectorcrawler.md) |Service containing APIs that are called during a crawl. |
|[ConnectorOAuth](/MicrosoftSearch/custom-connector-sdk-contracts-connectoroauth.md) |Service for OAuth flows like refreshing access token during crawls. |

You can download these contract protocol buffer files from [here](https://github.com/microsoftgraph/msgraph-connectors-sdk/tree/main/Contracts).
