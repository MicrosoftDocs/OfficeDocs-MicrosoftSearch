---
title: "Graph connectors SDK Contracts Connector OAuth API"
ms.author: rchanda
author: rchanda
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
description: "Graph connectors SDK Contracts Connector OAuth API"
---

# Connector OAuth APIs and Models

## Connector OAuth APIs

|Method |Parameters |Return Type |Description |
|:----------|:-------------|:----------|:----------|
|RefreshAccessToken |RefreshAccessTokenRequest |RefreshAccessTokenResponse |This API is used to generate a refreshed token from the auth server of the datasource and send the token details to the platform. |

## Connector OAuth API Models

**RefreshAccessTokenRequest**: Request model for refreshing the OAuth token.

|Property |Type |Description |
|:----------|:-------------|:----------|
|authenticationData |AuthenticationData |Holds data source access URL and credential to access the datasource along with current token information. |

**RefreshAccessTokenResponse**: Response model for Refresh OAuth token request.

|Property |Type |Description |
|:----------|:-------------|:----------|
|status |OperationStatus |Status of operation and error details in case of error |
|refreshedCredentialData |OAuth2ClientCredentialsResponse |Credential data containing refreshed token information |
