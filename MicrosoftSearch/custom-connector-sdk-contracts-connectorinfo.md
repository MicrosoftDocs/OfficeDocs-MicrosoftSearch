---
title: "Graph connectors SDK Contracts ConnectorInfo API"
ms.author: rchanda
author: rchanda
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
description: "Graph connectors SDK Contracts ConnectorInfo API"
---

# Connector Info APIs and Models

## Connector Info APIs

|Method |Parameters |Return Type |Description |
|:----------|:-------------|:----------|:-------------|
|GetBasicConnectorInfo |GetBasicConnectorInfoRequest |GetBasicConnectorInfoResponse |This API is used to get basic information of the connector. Currently it will be used by the platform to fetch the unique Connector ID. |
|HealthCheck |HealthCheckRequest |HealthCheckResponse |API to check if platform can communicate with the connector server. |

## Connector Info API Models

**GetBasicConnectorInfoResponse**: Response model holding basic connector information

|Property |Type |Description |
|:----------|:-------------|:----------|
|connectorId |String  |Unique identifier for the connector. This should be the unique guid of the connector. |

**GetBasicConnectorInfoRequest**: Request model to retrieve basic connector information. It does not have any properties currently; it will be added in future as required.

**HealthCheckRequest**: Request model for HealthCheck API. It does not have any properties currently, it will be added in future as required.

**HealthCheckResponse**: Response model for HealthCheck API. It does not have any properties currently, it will be added in future as required.
