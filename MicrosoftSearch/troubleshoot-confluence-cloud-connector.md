---
ms.date: 09/06/2021
title: "Troubleshooting guide for Confluence Cloud Microsoft Graph connector"
ms.author: kam1
author: TheKarthikeyan
manager: harshkum
audience: Admin
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Troubleshoot issues with Confluence Cloud Graph connector for Microsoft Search"
---

# Troubleshooting guide for Confluence Cloud Microsoft Graph connector

### 1. **Common errors observed while configuring the connector and their possible reasons are listed below.**

| Configuration step | Error message | Possible reason(s) |
| ------------ | ------------ | ------------ |
| Connection settings | The request is malformed or incorrect. | Incorrect Confluence site URL |
| Connection settings | Unable to reach the Confluence cloud service for your Confluence site. | Incorrect Confluence site URL |
| Connection settings | The client doesn't have permission to perform the action. | Invalid API token provided for Basic auth |
| Select properties | No error message and no preview results | Check your CQL query whether it is valid |

If you have any other issues or want to provide feedback, write to us [aka.ms/TalkToGraphConnectors](https://developer.microsoft.com/en-us/graph/support)