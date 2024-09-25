--- 
ms.date: 08/28/2024 
title: "Troubleshooting the File Share Microsoft Graph connector" 
ms.author: gladysa
author: gladysa
manager: brian.jackett
audience: Admin 
ms.audience: Admin 
ms.topic: article 
ms.service: mssearch 
ms.localizationpriority: medium 
description: "Troubleshooting the File Share Graph connector for Microsoft Search and Microsoft 365 Copilot" 
--- 

# Troubleshooting guide for File Share Microsoft Graph connector  

### 1. **The following are common errors observed while configuring the connector, or during crawling, and its possible reasons.**

| Configuration step | Error message | Possible reason(s) |
| ------------ | ------------ | ------------ |
| Authentication | There are some errors with file paths or URLs. *The Graph connector agent associated with the connection is not reachable.* | Check if the agent is running or if the app credentials have been expired or revoked. Refer to [Graph connector agent troubleshooting](./graph-connector-agent.md#troubleshooting)  |
| Authentication | There are some errors with file paths or URLs. *No files were found in the path provided. The client doesn't have permission to perform the action.* | Check if the path is correct and the account provided has access to the files. |
| Authentication | There are some errors with file paths or URLs. *The user account provided does not have permissions for the files in this location.*  | Check if the client does have permission to perform the action, if the path is correct and the account provided has access to the files. |
| Authentication | There are some errors with file paths or URLs. *Incorrect username or password.* | Check the authentication details with the data source. The username or password is incorrect, if the credentials are not correct, we don't check the file path access. |
| Crawling | There are some errors with file paths or URLs. *You don't have permission to access this data source. You can contact the owner of this data source to request permission. “Preserve Last Access" is enabled for the connection which requires "write" permissions on the file to update the access time.* | Check if "write" permissions are provided to the file/root directory. This occurs when provided credentials do not have 'Write' permission needed to preserve file's last access time. |

To get more information on the types of errors, go to the **error details** page after selecting the connection. Select the **error code** to see more detailed errors. Also refer to [Monitor your connections](./manage-connector.md) to learn more. 
