---
title: "Connectors preview"
ms.author: monaray
author: monaray97
manager: shohara
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Find out about Microsoft Graph Connectors preview for Microsoft Search."
---

# Microsoft Graph connectors preview release and features

Microsoft Graph connectors and Microsoft Search APIs are now generally available. The initial rollout will be to customers configured for Targeted Release. Upon rollout completion to all tenants, index quota utilization from connectors content will become subject to billing. See [Licensing requirements and pricing](licensing.md) for more information.

## Set up Targeted release

If you want to use Graph connectors in your tenant during rollout, you must opt into Targeted release. To learn more about the Targeted release option and how to set it, see [Set up the Standard or Targeted release options in Office 365](https://docs.microsoft.com/office365/admin/manage/release-options-in-office-365?view=o365-worldwide).

## Preview features

Although Microsoft Graph connectors and Microsoft Search APIs are now generally available, there are several features that will remain in preview.

The set of connectors and features in preview include:

* [Azure DevOps connector](azure-devops-connector.md)
* [Salesforce connector](salesforce-connector.md)
* [ServiceNow connector](servicenow.md) with search permissions that use source ACLs
* [Result cluster experience](result-cluster.md)

## Limitations

The following are known limitations:

* Ingestion throughput is throttled at about four items per second.

* There's no support for schema updates. After you create a connection setup, there's no way to update the schema. You can only delete and re-create the connection.

* There's a connections limit. Each tenant can create up to 10 connections.

* Edit support for connection is not available. Once the connection has been created, you cannot edit or change it. If you need to change any details, you must delete and recreate the connection.
