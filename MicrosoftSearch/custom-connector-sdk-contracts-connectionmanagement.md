---
title: "Graph connectors SDK Contracts Connection Management API"
ms.author: rchanda
author: rchanda1392
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.date: 06/29/2022
description: "Graph connectors SDK Contracts Connection Management API"
---

# Connection management APIs and Models

These APIs are called during the process of custom connector connection creation on Microsoft 365 admin center.

## Connection management APIs

|Method |Parameters |Return Type |Description |
|:----------|:-------------|:----------|:-------------|
|ValidateAuthentication |[ValidateAuthenticationRequest](#validateauthenticationrequest) |[ValidateAuthenticationResponse](#validateauthenticationresponse) |This API is called during custom connector connection creation on Microsoft 365 admin center. The API is used to validate the credentials and data source path provided by the admin in the connection settings step. |
|ValidateCustomConfiguration |[ValidateCustomConfigurationRequest](#validatecustomconfigurationrequest) |[ValidateCustomConfigurationResponse](#validatecustomconfigurationresponse) |This API is called during custom connector connection creation on Microsoft 365 admin center. The API is used to validate the optional configuration provided by the admin in connection configuration step. If no configuration is required for the connector, this API can just return a success response. |
|GetDataSourceSchema |[GetDataSourceSchemaRequest](#getdatasourceschemarequest) |[GetDataSourceSchemaResponse](#getdatasourceschemaresponse) |This API is called during custom connector connection creation on Microsoft 365 admin center. The API is used to get the data source schema in the format that can be understood by Microsoft Graph. More details are present [here](/graph/api/resources/externalconnectors-schema). |

### Connection management API Models

#### ValidateAuthenticationRequest

Request model to validate authentication to data source

|Property |Type |Description |
|:----------|:-------------|:----------|
|authenticationData |[AuthenticationData](/microsoftsearch/custom-connector-sdk-contracts-common#authenticationdata) |Holds data source access URL and credential to access it. |

#### ValidateAuthenticationResponse

Response model of validate authentication request to data source

|Property |Type |Description |
|:----------|:-------------|:----------|
|status |[OperationStatus](/microsoftsearch/custom-connector-sdk-contracts-common#operationstatus) |Status of operation and error details in case of error. |
|oAuth2ClientCredentialResponse |[OAuth2ClientCredentialResponse](/microsoftsearch/custom-connector-sdk-contracts-common#oauth2clientcredentialresponse) |Credential information to be sent to the connector during the crawl in case of OAuth flow (Access token, refresh token etc., which is sent by the auth server). This property need not be set for non-OAuth flows. |

#### ValidateCustomConfigurationRequest

Request model to validate custom configuration information

|Property |Type |Description |
|:----------|:-------------|:----------|
|customConfiguration |[CustomConfiguration](/microsoftsearch/custom-connector-sdk-contracts-common#customconfiguration) |Configuration data provided for the connector. |
|authenticationData |[AuthenticationData](/microsoftsearch/custom-connector-sdk-contracts-common#authenticationdata) |Holds data source access URL and credential to access it. |

#### ValidateCustomConfigurationResponse

Response model of validation of custom configuration information

|Property |Type |Description |
|:----------|:-------------|:----------|
|status |[OperationStatus](/microsoftsearch/custom-connector-sdk-contracts-common#operationstatus) |Status of operation and error details in case of error. |

#### GetDataSourceSchemaRequest

Request model to get schema information of data source

|Property |Type |Description |
|:----------|:-------------|:----------|
|customConfiguration |[CustomConfiguration](/microsoftsearch/custom-connector-sdk-contracts-common#customconfiguration) |Configuration data provided for the connector. |
|authenticationData |[AuthenticationData](/microsoftsearch/custom-connector-sdk-contracts-common#authenticationdata) |Holds data source access URL and credential to access it. |

#### GetDataSourceSchemaResponse

Response model of data source schema request

|Property |Type |Description |
|:----------|:-------------|:----------|
|status |[OperationStatus](/microsoftsearch/custom-connector-sdk-contracts-common#operationstatus) |Status of operation and error details in case of error. |
|dataSourceSchema |[DataSourceSchema](/microsoftsearch/custom-connector-sdk-contracts-common#datasourceschema) |Data source schema. More details about schema are present [here](/graph/api/resources/externalconnectors-schema). |
