---
title: "Microsoft Graph connectors SDK contracts connector OAuth API"
ms.author: rchanda
author: rchanda1392
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.date: 06/29/2022
description: "Microsoft Graph connectors SDK contracts connector OAuth API"
---

# Microsoft Graph connectors SDK contracts connector OAuth API

The Microsoft Graph connectors SDK contracts connector OAuth API is used for OAuth flows like refreshing access tokens during crawls.

## Connector OAuth APIs

This API is used to generate a refreshed token from the auth server of the data source and send the token details to the platform.

|Method |Parameters |Return Type |Description |
|:----------|:-------------|:----------|:----------|
|RefreshAccessToken |[RefreshAccessTokenRequest](#refreshaccesstokenrequest) |[RefreshAccessTokenResponse](#refreshaccesstokenresponse) | Shows the refreshed access token. |

### Connector OAuth API Models

#### RefreshAccessTokenRequest

Request model for refreshing the OAuth token.

|Property |Type |Description |
|:----------|:-------------|:----------|
|authenticationData |[AuthenticationData](/microsoftsearch/custom-connector-sdk-contracts-common#authenticationdata) |Holds the data source access URL, the credentials to access the data source and current token information. |

#### RefreshAccessTokenResponse

Response model for Refresh OAuth token request.

|Property |Type |Description |
|:----------|:-------------|:----------|
|status |[OperationStatus](/microsoftsearch/custom-connector-sdk-contracts-common#operationstatus) |Shows the status of the operation and details like error messages. |
|refreshedCredentialData |[OAuth2ClientCredentialsResponse](/microsoftsearch/custom-connector-sdk-contracts-common#oauth2clientcredentialsresponse) |Holds the refreshed token information. |
