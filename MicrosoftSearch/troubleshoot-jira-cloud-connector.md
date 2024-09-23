---
title: "Troubleshooting the Atlassian Jira Cloud Microsoft Graph connector"
ms.author: mecampos
author: mecampos
manager: umas
audience: Admin
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
description: "Troubleshooting the Atlassian Jira Cloud Graph connector for Microsoft Search and Microsoft 365 Copilot  "
ms.date: 07/22/2021
---

# Troubleshooting the Atlassian Jira Cloud Microsoft Graph connector

The following are common errors observed while configuring the connector, or during crawling, and their possible reasons.

| Step | Error message | Possible reason(s) |
|:------------ |:------------ |:------------|
| Connection settings | The request is malformed or incorrect. | Incorrect Jira site URL.|
| Connection settings | Unable to reach the Jira cloud service for your Jira site. | Incorrect Jira site URL.|
| Connection settings | The client doesn't have permission to perform the action. | Invalid API token provided for Basic auth.|
| Connection settings | "Something went wrong" error in OAuth pop-up window. | The scopes granted to OAuth app don't match. The mismatched scopes are listed in the pop-up window.|
| Crawl time (post connector configuration) | Can't authenticate with the data source. Verify the credentials associated with this data source are correct.| The user doesn't have one or more permissions required to crawl Jira.|
| Crawl time (post connector configuration) | You don't have permission to access this data source. You can contact the owner of this data source to request permission. | If you're using OAuth, the app scopes may have changed, or the app may have expired or deleted. <br> If you're using basic authentication, the API token may have expired or deleted.|
| Crawl time (post connector configuration) | Error code: 1003 - You don't have permission to access this data source. <br> Detailed error code: 7612 | The crawl account does not have "browse projects" permission for the listed project (under the 'item ID' column). |

If you have issues or want to provide feedback, contact [Microsoft Graph | Support](https://developer.microsoft.com/en-us/graph/support).
