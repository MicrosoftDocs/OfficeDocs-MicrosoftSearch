--- 
ms.date: 09/11/2024 
title: "Troubleshooting the CSV Microsoft Graph connector" 
ms.author: gladysa
author: gladysa
manager: brian.jackett
audience: Admin 
ms.audience: Admin 
ms.topic: article 
ms.service: mssearch 
ms.localizationpriority: medium 
description: "Troubleshooting the CSV Graph connector for Microsoft Search and Microsoft 365 Copilot" 
--- 

# Troubleshooting the CSV Microsoft Graph connector 

### Review "spaces" in the CSV header which results in errors while trying to authenticate
No spaces are allowed in headers. Not only leading or trailing spaces, but no spaces allowed even in the middle of the header name.

To view more error types,  select the connection and click **error details** > **error code**. For more information, see [Monitor your connections](./manage-connector.md)