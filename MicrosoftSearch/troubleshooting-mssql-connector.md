---
ms.date: 10/08/2019
title: "Troubleshooting guide for Azure SQL and Microsoft SQL Server Microsoft Graph connector for Microsoft Search"
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
description: "Troubleshoot issues with the Azure SQL and Microsoft SQL Microsoft Graph connector for Microsoft Search."
---

# Troubleshooting guide for Azure SQL and Microsoft SQL Microsoft Graph connector

### 1. **The following is a common error observed while configuring the connector, and its possible reason.**

| Configuration step | Error message | Possible reason(s) |
| ------------ | ------------ | ------------ |
| Full crawl | `Error from database server: A transport level error has occurred when receiving results from the server.` | This error arises due to network issues. It is recommended to check network logs using [Microsoft network monitor](https://www.microsoft.com/download/details.aspx?id=4865) and reach out to Microsoft customer support. |
| Full crawl | `Column column_name returned from full crawl SQL query contains non-alphanumeric character` | Non-alphanumeric characters (like underscores) are not allowed in column names in SELECT clause. Use aliases to rename columns and remove non-alphanumeric characters (Example - SELECT column_name AS columnName). |

If you have any other issues or want to provide feedback, write to us [aka.ms/TalkToGraphConnectors](https://aka.ms/TalkToGraphConnectors).