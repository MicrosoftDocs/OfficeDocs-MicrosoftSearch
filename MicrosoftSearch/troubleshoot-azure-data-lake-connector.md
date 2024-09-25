--- 
ms.date: 09/11/2024 
title: "Troubleshooting the Azure Data Lake Storage Gen2 Microsoft Graph connector" 
ms.author: gladysa
author: gladysa
manager: brian.jackett
audience: Admin 
ms.audience: Admin 
ms.topic: article 
ms.service: mssearch 
ms.localizationpriority: medium 
description: "Troubleshoot issues with the Azure Data Lake Storage Gen2 Graph connector for Microsoft Search" 
--- 

# Troubleshooting guide for Azure Data Lake Storage Gen2 Microsoft Graph connector 

### 1. **Common errors observed while configuring the connector and their possible reasons are listed below.**

| Configuration step | Error message | Possible reason(s) |
| ------------ | ------------ | ------------ |
| Connection settings | The connection fails even after allowing the public IP address in the ADLS firewall settings. |  Allow access to the VNet and the IP (for disaster recovery purposes) using a PowerShell command, as there is no option to do that in the Azure portal. |
| Connection settings | InvalidConfigurationException |  Check if you have setup a valid storage for crawls but would have later deleted the storage account which will end up in this situation. |

To get more information on the types of errors, go to the **error details** page after selecting the connection. Select the **error code** to see more detailed errors. Also refer to [Monitor your connections](./manage-connector.md) to learn more. 
