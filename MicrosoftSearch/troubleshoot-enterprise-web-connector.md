---
ms.date: 10/08/2019
title: "Troubleshooting the Enterprise Websites Microsoft Graph connector"
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
description: "Troubleshooting the Enterprise websites Microsoft Graph connector for Microsoft Search and Microsoft 365 Copilot"
---

# Troubleshooting the Enterprise Websites Microsoft Graph connector

The following common errors are observed while configuring the connector, or during crawling and their possible reasons.

Detailed Error code | Error message
|:--- |:---|
|6001 | The site that is being tried to index isn't reachable.|
|6005 | The source page that is being tried to index has been blocked by robots.txt configuration.|
|6008 | Unable to resolve the DNS.|
|6009 | For all client-side errors (except HTTP 404, 408), refer to HTTP 4xx error codes for details.|
|6013 | The source page that is being tried to index couldn't be found. (HTTP 404 error).|
|6018 | The source page isn't responding, and the request has timed out. (HTTP 408 error).|
|6021 | The source page that is being tried to index has no textual content on the page.|
|6023 | The source page that is being tried to index is unsupported (not an HTML page).|
|6024 | The source page that is being tried to index has unsupported content.|

* Errors 6001-6013 occur when the data source isn't reachable due to a network issue or when the data source itself is deleted, moved, or renamed. Check if the data source details provided are still valid.
* Errors 6021-6024 occur when the data source contains non-textual content on the page or when the page isn't HTML. Check the data source and add this page to the exclusion list or ignore the error.

If you have any other issues or want to provide feedback, write to us [aka.ms/TalkToGraphConnectors](https://aka.ms/TalkToGraphConnectors).
