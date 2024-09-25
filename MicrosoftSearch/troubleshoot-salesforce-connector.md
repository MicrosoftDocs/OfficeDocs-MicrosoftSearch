--- 
ms.date: 09/11/2024 
title: "Troubleshooting guide for Salesforce Microsoft Graph connector" 
ms.author: gladysa
author: gladysa
manager: brian.jackett 
audience: Admin 
ms.audience: Admin 
ms.topic: article 
ms.service: mssearch 
ms.localizationpriority: medium 
description: "Troubleshoot issues with the Salesforce Graph connector for Microsoft Search" 
--- 

# Troubleshooting guide for Salesforce Microsoft Graph connector 

### 1. **Bad state error while signing-in to create a connection**
![Salesforce bad state error message](media/salesforce-connector/sf-bad-state-troubleshoot.png)
The PKCE option is checked in the application, causing the issue. To fix it, uncheck this option in the app registration in Salesforce.

![Salesforce PKCE checkbox](media/salesforce-connector/sf-pkce-troubleshoot.png)

### 2. **OAuth app scope names have changed**
The name of the selected OAuth scopes changed to the following names: 

- Access and manage your data (API) is now = **Manage user data via APIs (api)**

- Perform requests on your behalf at any time (refresh_token, offline_access) is now = **Perform requests at any time**

### 3. **Insufficient permissions**
Review the setup of the configured user profile. The `View Setup and Configuration` must be checked and the API must be enabled for `Org` and `Profile`.

 ![Salesforce view setup and configuration permission](media/salesforce-connector/sf-view-setup-troubleshoot.png)

To get more information on the types of errors, go to the **error details** page after selecting the connection. Select the **error code** to see more detailed errors. Also refer to [Monitor your connections](./manage-connector.md) to learn more.