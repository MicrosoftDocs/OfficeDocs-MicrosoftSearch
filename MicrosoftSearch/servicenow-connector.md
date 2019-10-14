---
title: "ServiceNow connector configuration in the M365 Admin portal"
ms.author: v-pamcn
author: TrishaMc1
manager: mnirkhe
ms.date: 10/08/2019
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Priority
search.appverid:
- BFB160
- MET150
- MOE150
description: "ServiceNow connector configuration in the M365 Admin portal."
---

# ServiceNow connector configuration in the M365 Admin portal

## Overview
The ServiceNow connector for Microsoft Search will allow your organization to index **knowledge base articles** that are visible to all users within your tenant. Once you have configured the connector and sync’d content from ServiceNow, the end user will then be able to search for those articles from any Microsoft Search client.   

This article is intended for M365 Search administrators, or anyone who is responsible for configuring, running, and monitoring the connector. Here you can find information on what to know before configuring your connector, how to get started, and additional information regarding connector capabilities, limitations, and troubleshooting techniques. 

## Things to know before configuring your connector
* Your organization’s ServiceNow instance URL: This will typically look like https:/?<your-organization-domain>.service-now.com 
* Credentials for an account in ServiceNow: You will need an account for setting up the connection to ServiceNow as well as for allowing Microsoft Search, represented by Microsoft Graph Connector service, to periodically sync the articles from ServiceNow based on refresh schedule. 
* Client ID and Client Secret for using OAuth for authentication with ServiceNow (refer to authentication topic below). 

## Authentication
The connector supports the following methods to authenticate and sync content from ServiceNow:   
* Basic authentication  
* OAuth (recommended) 

 In order to use OAuth for authentication, the ServiceNow admin needs to provision an endpoint in your ServiceNow instance to allow clients (the Microsoft Search app in this case) to access the instance.  

While this sounds complicated, it’s actually quite straightforward. Refer to ServiceNow documentation on [how to create an OAuth endpoint for clients to access your instance](https://docs.servicenow.com/bundle/newyork-platform-administration/page/administer/security/task/t_CreateEndpointforExternalClients.html). 

Use the following guidance for filling out the endpoint creation form: 

**Field** | **Description** | **Recommended Value**
--- | --- | ---
Name | A unique name that identifies the application that you require OAuth access for. | Microsoft Search 
Client ID | [Read-Only] The auto-generated unique ID of the application. The instance uses the client ID when requesting an access token. | N/A
Client Secret | The shared secret string that both the ServiceNow instance and the client application (Microsoft Search in this case) will use to authorize communications with one another. | Follow security best-practices by treating this as a password.
Redirect URL | [Required] The CALLBACK URL that the authorization server redirects to. | https://gcs.office.com/v1.0/admin/oauth/callback
Logo URL | The URL that contains an image to use as the application logo | N/A
Active | Select the check box to make the application registry active. | Set to active
Refresh Token Lifespan | The number of seconds that a refresh token is valid. By default, refresh tokens expire in 100 days (8640000 seconds). | 31,536,000 (i.e. 1 year) 
Access Token Lifespan | The number of seconds that an access token is valid. | 43,200 (i.e. 12 hours)

The **Client ID** and **Client Secret** that is created from the above step will be required when configuring the connector using OAuth.

## Sync filter
The sync filter enables you to specify conditions for sync’ing articles – this is similar to a Where clause in a SQL Select statement. For example, you can choose to index of only articles which are published and active. The configuration page within product outlines the steps on how to capture and set the Sync filter.

## ACLs
The ServiceNow connector only supports indexing articles which are visible to any user with your tenant.  

## Set refresh schedule
The ServiceNow connector supports refresh schedules for both full-sync and incremental-sync. It is recommended to set both. The full-sync schedule is required to detect deletes of articles previously synced to Microsoft Search index as well as articles which moved out of the sync filter. When first connecting to the service, a full crawl is needed to sync all the knowledge base articles. However, an incremental sync is required for syncing new items and making updates.

