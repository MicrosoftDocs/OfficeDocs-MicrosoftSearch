---
ms.date: 09/03/2024
title: "Deploy Microsoft Graph connectors in Teams admin center"
ms.author: muwagerikpe
author: muwagerikpe
manager: rajun
audience: Admin
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
description: "Learn how to deploy partner-built Microsoft Graph connectors with a single click in Teams admin center, so you can index content that participates in experiences such as Copilot for Microsoft 365 and Microsoft Search."
---

# Deploy Microsoft Graph connectors in Teams admin center

This article describes how to deploy partner-built Microsoft Graph connectors with a single click in Teams admin center. These Microsoft Graph connectors will index content from these partners into Microsoft Graph, so that content can participate in experiences such as Copilot for Microsoft 365, Microsoft Search, and more.

## Partners with Microsoft Graph connector Teams apps
Currently, the following partners have Graph connectors that can be deployed from Teams admin center:
- [Tigerhall](https://admin.teams.microsoft.com/policies/manage-apps/682912ef-28b1-49d1-889f-ea6a1ef6d198/graph-connector)

## Deploying a Microsoft Graph connector Teams apps
You will need to take the following steps to deploy a Microsoft Graph connector Teams app:
1. Sign into [Teams admin center](https://admin.teams.microsoft.com/) as a Global admin or Teams admin of the tenant.
2. Select the **Manage apps** blade in the left rail.
3. Search for your desired app in the search bar.
4. On the detail page of the Teams app, navigate to the **Permissions** tab and ensure you grant consent to the requested permissions.
5. On the detail page of the Teams app, navigate to the **Graph Connector**, and click the **Connection status** toggle.
6. Wait while the connection is in progress. Once you enable the Microsoft Graph connector, the Connection status is **on** in Teams admin center. At this point, you manage the Microsoft Graph connector from the [Data Sources tab](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/Connectors) in Microsoft 365 admin center's Search & Intelligence portal.
7. If you want to delete the Microsoft Graph connector, you can do so by turning off the Connection status toggle in Teams admin center or deleting the Microsoft Graph connector in the Data sources tab.

![simplified admin experience in the Teams admin center](media/oneclickadmin-TAC-connectors.png)
