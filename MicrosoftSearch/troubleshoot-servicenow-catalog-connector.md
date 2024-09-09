---
ms.date: 10/08/2019
title: "Troubleshooting the ServiceNow Catalog Microsoft Graph connector"
ms.author: kam1
author: TheKarthikeyan
manager: harshkum
audience: Admin
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Troubleshooting the ServiceNow Catalog Microsoft Graph connector for Microsoft Search and Microsoft 365 Copilot"
---
# Troubleshooting the ServiceNow Catalog Microsoft Graph connector
The following common errors are observed while configuring the connector, or during crawling and their possible reasons.

### 1. Unable to sign in due to Single Sign-on enabled ServiceNow instance

If your organization has enabled Single Sign-on (SSO) to ServiceNow, you may have trouble logging in with the service account. You can bring up username and password-based sign-in by adding <em> `login.do`</em> to the ServiceNow instance URL. Example: `https://<your-organization-domain>.service-now.com./login.do`.

### 2. Unauthorized or forbidden response to API request

#### 2.1. Check table access permissions

If you see forbidden or unauthorized response in connection status, check if the service account has required access to the tables mentioned in [step 3: connection settings](./servicenow-catalog-connector.md#step-3-connection-settings). Check whether all the columns in the tables have read access.

#### 2.2. Change in account password

The connector uses an access token fetched on behalf of the service account for the crawl. The access token refreshes every 12 hours. Ensure that the service account password isn't changed after publishing the connection. You may need to reauthenticate the connection if there's a password change.

#### 2.3. Check if the ServiceNow instance behind the firewall

Your Microsoft Graph connector may not be able to reach your ServiceNow instance if it is behind a network firewall. You'll need to explicitly allow access to the connector service. You can find the public IP address range of the connector service in the table below. Based on your tenant region, add it to your ServiceNow instance network allowlist.

 Environment | Region | Range
--- | --- | ---
PROD | North America | 52.250.92.252/30, 52.224.250.216/30
PROD | Europe | 20.54.41.208/30, 51.105.159.88/30
PROD | Asia Pacific | 52.139.188.212/30, 20.43.146.44/30

#### 2.4. Access permissions not working as expected

If you observe discrepancies in access permissions applied to search results, verify user criteria configuration in [applying user criteria to catalog items](https://docs.servicenow.com/bundle/orlando-it-service-management/page/product/service-catalog-management/task/t_AppUserCritItemsCat.html).

### 3. Issues with *Only people with access to this data source* permission

#### 3.1 Unable to choose *Only people with access to this data source*

You may not be able to choose *Only people with access to this data source* option if the service account doesn't have read permissions to the required tables in [step 3: connection settings](./servicenow-catalog-connector.md#step-3-connection-settings). Check whether the service account can read tables mentioned under *Index and support user criteria permissions* feature.

#### 3.2 User mapping failures

 ServiceNow user accounts that don't have a Microsoft 365 user in Microsoft Entra ID won't map. Non-user, service accounts are expected to fail user mapping. The number of user mapping failures can be accessed in the identity stats area in the connection detail window. Log of failed user mappings can be downloaded from the error tab.

### 4. Issues with user criteria access flow

If you see differences in the user criteria validation between ServiceNow and Microsoft Search, set `glide.knowman.block_access_with_no_user_criteria` system property to `no`.

If you have any other issues or want to provide feedback, write to us [aka.ms/TalkToGraphConnectors](https://aka.ms/TalkToGraphConnectors)
