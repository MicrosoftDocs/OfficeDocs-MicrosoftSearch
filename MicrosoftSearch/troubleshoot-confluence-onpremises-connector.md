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
ms.localizationpriority: high
search.appverid:
- BFB160
- MET150
- MOE150
description: "Troubleshoot issues with the Confluence On-premises Graph Microsoft connector for Microsoft Search"
---
# Troubleshooting guide for Confluence On-premises Microsoft Graph connector

## 1. **The common errors that can be seen while configuring the connector and their possible reasons are listed below.**

| Configuration step | Error message | Possible reason(s) |
| ------------ | ------------ | ------------ |
| Connection settings | The request is malformed or incorrect. | Incorrect Confluence site URL |
| Connection settings | Unable to reach the Confluence On-premises service for your Confluence site. | Incorrect Confluence site URL |
| Connection settings | The client doesn't have permission to perform the action. | Invalid password provided for Basic auth |
| Select properties | No preview results | Check your CQL query whether it's valid and matches the content to crawl |

If you have any other issues or want to provide feedback, write to us [aka.ms/TalkToGraphConnectors](https://developer.microsoft.com/en-us/graph/support).

## 2. Test your connection
a) To check active pages on confluence instance <br>
b) To check the list of spaces that account has access to

Run the URL mentioned below in browser or postman with the same cred used for connection creation.

> [!NOTE]
> Confluence space API will fetch maximum 500 spaces in a call, so we can split the request if we have more spaces.

The URL is <ConfluenceURL/rest/api/space?limit=500&start=0>.

At the end of response, we can see output similar to:

"start":0,<br>
"limit":500,<br>
"size":500,<br>

For more than 500 pages, to get the next set of pages of response, run the URL in the format that follows.
The URL is <ConfluenceURL/rest/api/space?limit=500&start=500>.
