---
title: "Troubleshooting the Azure DevOps Wiki Microsoft Graph connector for Microsoft Search and Microsoft 365 Copilot"
ms.author: vivg
author: vivg
manager: harshkum
audience: Admin
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: Medium
search.appverid:
- BFB160
- MET150
- MOE150
description: "Troubleshooting the Azure DevOps Wiki Microsoft Graph connector for Microsoft Search and Microsoft 365 Copilot"
ms.date: 06/03/2022
---

# Troubleshooting the Azure DevOps Wiki Microsoft Graph connector

The following common errors are observed while configuring the connector or during crawling and their possible reason.

| Step | Error message | Possible reason|
|:------------ |:------------ |:------------ |
| Connection settings | `Invalid credentials detected. Try signing in with a different account or check the permissions for your account`  *Third-party application access via OAuth* may be disabled. Follow the steps to [manage security policies].|(/azure/devops/organizations/accounts/change-application-access-policies?view=azure-devops#manage-a-policy&preserve-view=true) to enable OAuth. |
| Connection settings | `Bad state` message in OAuth pop-up window with URL stating `error=InvalidScope` | Wrong scopes provided to the registered app. |
| Connection settings | `400 - Bad request` message in OAuth pop-up window | Incorrect App ID.|
| Connection settings | `BadRequest: Bad request on API request` message in OAuth pop-up window | Incorrect client secret.|
| Crawl time (post connector configuration) | `The account associated with the connector doesn't have permission to access the item.` | The registered app doesn't have any of the required OAuth scopes. |
| Crawl time (post connector configuration) | `You don't have permission to access this data source. You can contact the owner of this data source to request permission.` | *Third-party application access via OAuth* is disabled. Follow steps to [manage security policies](/azure/devops/organizations/accounts/change-application-access-policies?view=azure-devops#manage-a-policy&preserve-view=true) to enable OAuth. |
| Crawl time (post connector configuration) | `Credentials associated with this data source have expired. Renew the credentials and then update the connection` | The registered app may is deleted or expired. |
| Crawl time (post connector configuration) | `Item listed but no longer accessible or no longer exists` | The crawling account may be missing 'Basic' access level. Crawls fail with 'Stakeholder' access. |

If you have issues or want to provide feedback, contact [Microsoft Graph | Support](https://developer.microsoft.com/en-us/graph/support).