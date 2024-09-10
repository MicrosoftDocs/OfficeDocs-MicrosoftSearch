---
ms.date: 06/11/2020
title: "Troubleshooting guide for Azure DevOps Work Items Microsoft Graph connector for Microsoft Search"
ms.author: mecampos
author: mecampos
manager: lsheppard
audience: Admin
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
description: "Troubleshoot issues with the Azure DevOps Work Items Microsoft Graph connector for Microsoft Search"
---
# Troubleshooting guide for Azure DevOps Work Items Microsoft Graph connector

### 1. **The following are common errors observed while configuring the connector, or during crawling, and its possible reasons.**

| Step | Error message | Possible reason(s) |
| ------------ | ------------ | ------------ |
| Connection settings | `Invalid Credentials detected. Try signing in with a different account or check the permissions for your account` | *Third-party application access via OAuth* may be disabled. Follow steps to [manage security policies](/azure/devops/organizations/accounts/change-application-access-policies?view=azure-devops#manage-a-policy&preserve-view=true) to enable OAuth. |
| Connection settings | `Bad state` message in OAuth pop-up window with URL stating `error=InvalidScope` | Wrong scopes provided to the registered app. |
| Connection settings | `400 - Bad request` message in OAuth pop-up window | Incorrect App ID |
| Connection settings | `BadRequest: Bad Request on api request` message in OAuth pop-up window | Incorrect Client secret |
| Crawl time (post connector configuration) | `The account associated with the connector doesn't have permission to access the item.` | The registered app does not have any of the required OAuth scopes. (Note - A new OAuth scope requirement 'Analytics:read' was introduced on 8/31/2021) |
| Crawl time (post connector configuration) | `You don't have permission to access this data source. You can contact the owner of this data source to request permission.` | *Third-party application access via OAuth* is disabled. Follow steps to [manage security policies](/azure/devops/organizations/accounts/change-application-access-policies?view=azure-devops#manage-a-policy&preserve-view=true) to enable OAuth. |
| Crawl time (post connector configuration) | `Credentials associated with this data source have expired. Renew the credentials and then update the connection` | The registered app may have been deleted or expired. |
| Crawl time (post connector configuration) | `Item listed but no longer accessible or no longer exists` | The crawling account may be missing 'Basic' access level. Crawls fail with 'Stakeholder' access. |

If you have any other issues or want to provide feedback, write to us [aka.ms/TalkToGraphConnectors](https://developer.microsoft.com/en-us/graph/support).