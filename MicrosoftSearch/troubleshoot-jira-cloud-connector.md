---
title: "Troubleshooting guide for Atlassian Jira Cloud Microsoft Graph connector"
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
description: "Troubleshoot issues with the Atlassian Jira Cloud Graph connector for Microsoft Search"
ms.date: 07/22/2021
---

# Troubleshooting guide for Atlassian Jira Cloud Microsoft Graph connector

### 1. **Below is a list of common errors observed while configuring the connector or during crawls, and their possible reasons.**

| Step | Error message | Possible reason(s) |
| ------------ | ------------ | ------------ |
| Connection settings | The request is malformed or incorrect. | Incorrect Jira site URL. |
| Connection settings | Unable to reach the Jira cloud service for your Jira site. | Incorrect Jira site URL. |
| Connection settings | The client doesn't have permission to perform the action. | Invalid API token provided for Basic auth. |
| Connection settings | "Something went wrong" error in OAuth pop-up window. | The scopes granted to OAuth app don't match. The mismatched scopes are listed in the pop-up window. |
| Crawl time (post connector configuration) | Can't authenticate with data source. Verify the credentials associated with this data source are correct. | The user doesn't have one or more permissions required to crawl Jira. |
| Crawl time (post connector configuration) | You don't have permission to access this data source. You can contact the owner of this data source to request permission. | If you're using OAuth, the app scopes may have changed, or the app may have expired or deleted. <br> If you're using basic authentication, the API token may have expired or deleted. |
| Crawl time (post connector configuration) | Error code: 1003 - You don't have permission to access this data source. <br> Detailed error code: 7612 | The crawl account does not have "Browse projects" permission for the listed project (under 'item id' column). |

If you have any other issues or want to provide feedback, write to us [aka.ms/TalkToGraphConnectors](https://aka.ms/TalkToGraphConnectors)