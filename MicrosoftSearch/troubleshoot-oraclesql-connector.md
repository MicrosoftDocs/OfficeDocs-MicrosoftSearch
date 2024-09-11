---
ms.date: 10/08/2019
title: "Troubleshooting the Oracle SQL Microsoft Graph connector"
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
ROBOTS: NoIndex
description: "Troubleshoot issues with the Oracle SQL Microsoft Graph connector for Microsoft Search and Microsoft 365 Copilot."
---

# Troubleshooting the Oracle SQL Microsoft Graph connector

The following common errors are observed while configuring the connector, or during crawling and their possible reasons.

| Configuration step | Error message | Possible reasons |
|:------------ |:------------ |:------------ |
| Database settings | `Error from database server: Connection request timed out` | Invalid hostname <br> host not reachable.|
| Database settings | `Error from database server: ORA-12541: TNS: No listener` | Invalid port.|
| Database settings | `Error from database server: ORA-12514: TNS: listener does not currently know of service requested in connector descriptor` | Invalid service (database) name.|
| Database settings | `Error from database server: Login failed for user 'user'.` | Invalid username or password.|
| Full crawl | `Column column_name returned from full crawl SQL query contains non-alphanumeric character` | Nonalphanumeric characters (like underscores) are not allowed in column names in the SELECT clause. Use aliases to rename columns and remove nonalphanumeric characters (Example - SELECT column_name AS columnName).|

If you have any other issues or want to provide feedback, write to us [aka.ms/TalkToGraphConnectors](https://aka.ms/TalkToGraphConnectors).

