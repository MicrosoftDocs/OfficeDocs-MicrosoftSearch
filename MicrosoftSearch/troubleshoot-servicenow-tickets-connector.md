---
ms.date: 10/08/2019
title: "Troubleshooting guide for ServiceNow Tickets Microsoft Graph connector"
ms.author: souravpoddar
author: souravpoddar001
manager: harshkum
audience: Admin
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
description: "Troubleshoot issues with the ServiceNow Tickets Graph connector for Microsoft Search and Copilot."
---
# Troubleshooting guide for ServiceNow Tickets Microsoft Graph connector

### 1. **Unable to log in due to single sign-On enabled ServiceNow instance**

If your organization has enabled single sign-On (SSO) to ServiceNow, you may have trouble logging in with the service account. You can bring up username and password based login by adding <em> `login.do`</em> to the ServiceNow instance URL. Example. `https://<your-organization-domain>.service-now.com./login.do`

### 2. **Unauthorized or forbidden response to API request**

#### 2.1. Check table access permissions
If you see forbidden or unauthorized response in connection status, check if the service account has required access to the tables mentioned in [step 3: connection settings](./servicenow-tickets-connector.md#step-3-connection-settings). Check whether all the columns in the tables have read access.

#### 2.2. Change in account password
The Microsoft Graph connector uses access token fetched on behalf of service account for crawl. The access token refreshes every 12 hours. Ensure that service account password isn't changed after publishing the connection. You may need to reauthenticate the connection if there's a change in password.

#### 2.3. Check if ServiceNow instance behind firewall
The Microsoft Graph Connector may not be able to reach your ServiceNow instance if it is behind a network firewall. You'll need to explicitly allow access to connector service. You can find public IP address range of connector service in the table below. Based on your tenant region, add it to your ServiceNow instance network allowlist.

**Environment** | **Region** | **Range**
--- | --- | ---
PROD | North America | 52.250.92.252/30, 52.224.250.216/30
PROD | Europe | 20.54.41.208/30, 51.105.159.88/30
PROD | Asia Pacific | 52.139.188.212/30, 20.43.146.44/30

#### 3. **Access permissions not working as expected**

If you observe discrepancies in access permissions applied to search results, verify whether the search user is part of `assigned_to` and `opened_by` fields.

### 4. **Issues with *Only people with access to this data source* permission**

#### 4.1 User mapping failures

 ServiceNow user accounts that don't have a Microsoft 365 user in Microsoft Entra ID won't map. Non-user, service accounts are expected to fail user mapping. Number of user mapping failures can be accessed in identity stats area in connection detail window. Log of failed user mappings can be downloaded from Error tab.

If you have any other issues or want to provide feedback, write to us [aka.ms/TalkToGraphConnectors](https://developer.microsoft.com/en-us/graph/support).
