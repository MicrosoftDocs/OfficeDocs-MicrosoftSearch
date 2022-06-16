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
|ConnectorInfo |Service containing APIs to get information about the connector. If you are using the visual studio extension, this has default implementation and you do not have to make any change. |
|ConnectionManagement |Service containing APIs which are called during the process of custom connector connection creation on M365 admin center. |
|ConnectorCrawl |Service containing APIs which are called during a crawl. |
|ConnectorOAuth |Service for OAuth flows like refreshing access token during crawls. |
