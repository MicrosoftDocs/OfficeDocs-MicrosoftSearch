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

# Troubleshooting guide for CSV Microsoft Graph connector 

### 1. **Review "spaces" in the CSV header which results in errors while trying to authenticate** 
No spaces are allowed in headers. Not only leading or trailing spaces, but no spaces allowed even in the middle of the header name.

To get more information on the types of errors, go to the **error details** page after selecting the connection. Select the **error code** to see more detailed errors. Also refer to [Monitor your connections](./manage-connector.md) to learn more.