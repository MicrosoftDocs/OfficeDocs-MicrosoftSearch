---
ms.date: 02/02/2022
title: "Troubleshooting guide for Confluence On-premises Microsoft Graph connector (Preview)"
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
description: "Troubleshoot issues with the Confluence On-premises Graph Microsoft connector for Microsoft Search"
---
# Troubleshooting guide for Confluence On-premises Microsoft Graph connector

### 1. **The common errors that can be seen while configuring the connector and their possible reasons are listed below.**

| Configuration step | Error message | Possible reason(s) |
| ------------ | ------------ | ------------ |
| Connection settings | The request is malformed or incorrect. | Incorrect Confluence site URL |
| Connection settings | Unable to reach the Confluence On-premises service for your Confluence site. | Incorrect Confluence site URL |
| Connection settings | The client doesn't have permission to perform the action. | Invalid password provided for Basic auth |
| Select properties | No preview results | Check your CQL query whether it's valid and matches the content to crawl |

### 1. **What kind of spaces do we index?**
We index only current spaces and not archived spaces.

If you have any other issues or want to provide feedback, write to us [aka.ms/TalkToGraphConnectors](https://aka.ms/TalkToGraphConnectors).