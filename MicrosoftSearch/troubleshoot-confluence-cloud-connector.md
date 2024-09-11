---
ms.date: 09/06/2021
title: "Troubleshooting the Confluence Cloud Microsoft Graph connector"
ms.author: kam1
author: TheKarthikeyan
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
description: "Troubleshooting the Confluence Cloud Microsoft Graph connector for Microsoft Search and Microsoft 365 Copilot"
---

# Troubleshooting the Confluence Cloud Microsoft Graph connector

The following common errors are observed while configuring the connector and their possible reasons.

| Configuration step |Error message | Possible reason(s)
|:------------ |:------------ |:------------ |
| Connection settings | The request is malformed or incorrect. | Incorrect Confluence site URL. |
| Connection settings | Unable to reach the Confluence cloud service for your Confluence site. | Incorrect Confluence site URL. |
| Connection settings | The client doesn't have permission to perform the action. | Invalid API token provided for Basic auth. |
| Select properties | No error message and no preview results | Check your CQL query whether it is valid. |

If you have any other issues or want to provide feedback, write to us [aka.ms/TalkToGraphConnectors](https://aka.ms/TalkToGraphConnectors)