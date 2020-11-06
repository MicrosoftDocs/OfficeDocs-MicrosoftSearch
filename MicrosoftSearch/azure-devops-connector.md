---
title: "Azure DevOps connector for Microsoft Search"
ms.author: shgrover
author: shakungrover05
manager: jeffkizn
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Set up the Azure DevOps connector for Microsoft Search"
---

# Azure DevOps connector

With the Azure DevOps connector, your organization can index work items in its instance of the Azure DevOps service. After you configure the connector and index content from Azure DevOps, end users can search for those items in Microsoft Search.

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors an Azure DevOps connector. It explains how to configure your connector and connector capabilities, limitations, and troubleshooting techniques.

>[!IMPORTANT]
>The Azure DevOps connector supports only the Azure DevOps cloud service. Azure DevOps Server 2019, TFS 2018, TFS 2017, TFS 2015, and TFS 2013 are not supported by this connector.

## Connect to a data source

To connect to your Azure DevOps instance, you need your Azure DevOps [organization](https://docs.microsoft.com/azure/devops/organizations/accounts/create-organization) name, its App ID, and client secret for OAuth authentication.

### Register an app

You must register an app in Azure DevOps so that the Microsoft Search app can access the instance. To learn more, see Azure DevOps documentation on how to [register an app](https://docs.microsoft.com/azure/devops/integrate/get-started/authentication/oauth?view=azure-devops#register-your-app).

The following table provides guidance on how to fill out the app registration form:

 **Mandatory Fields** | **Description**      | **Recommended Value**
--- | --- | ---
| Company Name         | This is the name of your company. | Use an appropriate value   |
| Application name     | This unique value identifies the application that you're authorizing.    | Microsoft Search     |
| Application website  | This required field is the URL of the application that will request access to your Azure DevOps instance during connector setup.  | <https://gcs.office.com/>                |
| Authorization callback URL        | A required callback URL that the authorization server redirects to. | <https://gcs.office.com/v1.0/admin/oauth/callback>|
| Authorized scopes | This is the scope of access for the application | Select the following scopes: Identity (read), Work Items (read), Variable Groups (read), Project and team (read), Graph (read)|

On registering the app with the details above, you will get the **App ID** and **Client Secret** that will be used to configure the connector.

>[!NOTE]
>To revoke access to any app registered in Azure DevOps, go to User settings at the right top of your Azure DevOps instance. Click on Profile and then click on Authorizations in the Security section of the side pane. Hover over an authorized OAuth app to see the Revoke button at the corner of the app details.

### Connection settings

After registering the Microsoft Search app with Azure DevOps, you can complete the connection settings step. Enter your organization name, App ID, and Client secret.

![Connection Application Settings](media/ADO_Connection_settings_2.png)

## Select projects and fields

You can choose for the connection to index either the entire organization or specific projects.

If you choose to index the entire organization, items in all projects in the organization will get indexed. New projects and items will be indexed during the next crawl after they are created. If you choose individual projects, only work items in those projects will be indexed.

![Configure data](media/ADO_Configure_data.png)

Next, select which fields you want the connection to index and preview data in these fields before proceeding.

![Choose properties](media/ADO_choose_properties.png)

## Manage search permissions

The Azure DevOps connector currently only supports search permissions **Visible to Everyone**. Indexed data will appear in the search results for all users.

## Manage search schema

Configure the search schema mapping. You can choose which properties to make **queryable**, **searchable** and **retrievable**.


## Set refresh schedule

The Azure DevOps connector supports refresh schedules for both full and incremental crawls. A full crawl finds deleted work items that were previously synced to the Microsoft Search index. A full crawl runs to sync all the work items. To sync new work items and updates to existing work items, you need to schedule incremental crawls.

The recommended schedule is one hour for an incremental crawl and one day for a full crawl.
