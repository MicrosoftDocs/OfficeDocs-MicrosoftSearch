---
title: "Graph connectors SDK Contracts Connection Management API"
ms.author: rchanda
author: rchanda
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
description: "Graph connectors SDK Contracts Connection Management API"
---

# Connection management APIs and Models

## Connection management APIs

|Method |Parameters |Return Type |Description |
|:----------|:-------------|:----------|:-------------|
|ValidateAuthentication |ValidateAuthenticationRequest |ValidateAuthenticationResponse |This API is called during custom connector connection creation on M365 admin center. The API is used to validate the credentials and data source path provided by the admin in the connection settings step. |
|ValidateCustomConfiguration |ValidateCustomConfigurationRequest |ValidateCustomConfigurationResponse |This API is called during custom connector connection creation on M365 admin center. The API is used to validate the optional configuration provided by the admin in connection configuration step. If no configuration is required for the connector, this API can simply return a success response. |
|GetDataSourceSchema |GetDataSourceSchemaRequest |GetDataSourceSchemaResponse |This API is called during custom connector connection creation on M365 admin center. The API is used to get the data source schema in the format which can be understood by Microsoft Graph. More details are present [here](/graph/api/resources/externalconnectors-schema?view=graph-rest-beta) |

## Connection management API Models

**ValidateAuthenticationRequest**: Request model to validate authentication to data source

|Property |Type |Description |
|:----------|:-------------|:----------|
|authenticationData |AuthenticationData |Holds data source access URL and credential to access it. |

**ValidateAuthenticationResponse**: Response model of validate authentication request to data source

|Property |Type |Description |
|:----------|:-------------|:----------|
|status |OperationStatus |Status of operation and error details in case of error. |
|oAuth2ClientCredentialsResponse |OAuth2ClientCredentialsResponse |Credential information to be sent to the connector during the crawl in case of OAuth flow (Access token, refresh token etc., which is sent by the auth server). This need not be set for non-OAuth flows. |

**ValidateCustomConfigurationRequest**: Request model to validate custom configuration information

|Property |Type |Description |
|:----------|:-------------|:----------|
|customConfiguration |CustomConfiguration |Configuration data provided for the connector. |
|authenticationData |AuthenticationData |Holds data source access URL and credential to access it. |

**ValidateCustomConfigurationResponse**: Response model of validation of custom configuration information

|Property |Type |Description |
|:----------|:-------------|:----------|
|status |OperationStatus |Status of operation and error details in case of error. |

**GetDataSourceSchemaRequest**: Request model to get schema information of data source

|Property |Type |Description |
|:----------|:-------------|:----------|
|customConfiguration |CustomConfiguration |Configuration data provided for the connector. |
|authenticationData |AuthenticationData |Holds data source access URL and credential to access it. |

**GetDataSourceSchemaResponse**: Response model of data source schema request

|Property |Type |Description |
|:----------|:-------------|:----------|
|status |OperationStatus |Status of operation and error details in case of error. |
|dataSourceSchema |DataSourceSchema |Data source schema. More details about schema are present [here](/graph/api/resources/externalconnectors-schema?view=graph-rest-beta). |
