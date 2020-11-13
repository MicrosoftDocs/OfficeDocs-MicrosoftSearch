---
title: "ServiceNow connector for Microsoft Search"
ms.author: kam1
author: TheKarthikeyan
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Set up the ServiceNow connector for Microsoft Search"
---


# ServiceNow connector

With the ServiceNow connector, your organization can index knowledge-base articles that are visible to all users or restricted with user criteria permissions within your organization. After you configure the connector and index content from ServiceNow, end users can search for those articles from any Microsoft Search client.  

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors a ServiceNow connector. It explains how to configure your connector and connector capabilities, limitations, and troubleshooting techniques.

Learn how to access Microsoft built connectors from [Set up your Microsoft-built connector for Microsoft Search](https://docs.microsoft.com/microsoftsearch/configure-connector). ServiceNow connector specific configuration is explained in the article below.

## Connection Settings
To connect to your ServiceNow data, you need your organization's **ServiceNow instance URL**, credentials for this account, and the Client ID and Client Secret for OAuth authentication.  

Your organization’s **ServiceNow instance URL** typically looks like **https://&lt;your-organization-domain>.service-now.com**. Along with this URL, you will need an account for setting up the connection to ServiceNow as well as for allowing Microsoft Search to periodically update the articles from ServiceNow based on the refresh schedule. The account should at least have <em>knowledge</em> role. [Learn how to assign role for ServiceNow accounts](https://docs.servicenow.com/bundle/paris-platform-administration/page/administer/users-and-groups/task/t_AssignARoleToAUser.html).

>[!NOTE]
>If you want to crawl user and group identities to honor access permissions of knowledge articles in Microsoft Search results, the account should have access to read the following table records in ServiceNow:
>* kb_uc_can_contribute_mtom
>* kb_uc_can_read_mtom
>* kb_uc_cannot_read_mtom
>* kb_uc_cannot_contribute_mtom
>* sys_user
>* sys_user_has_role
>* sys_user_grmember
>* user_criteria
>* kb_knowledge_base  
>To learn about setting read access to table records, see [Securing Table Records](https://developer.servicenow.com/dev.do#!/learn/learning-plans/orlando/new_to_servicenow/app_store_learnv2_securingapps_orlando_securing_table_records).

To authenticate and sync content from ServiceNow, choose **one of three** supported methods: 
1. Basic authentication 
2. ServiceNow OAuth (recommended)
3. Azure AD OpenID Connect

#### Basic authentication

Enter the username and password of ServiceNow account with **knowledge** role to authenticate to your instance.

#### ServiceNow OAuth

To use ServiceNow OAuth for authentication, a ServiceNow admin needs to provision an endpoint in your ServiceNow instance, so that the Microsoft Search app can access the instance. To learn more, see [Create an endpoint for clients to access the instance](https://docs.servicenow.com/bundle/newyork-platform-administration/page/administer/security/task/t_CreateEndpointforExternalClients.html) in the ServiceNow documentation.

The following table provides guidance on how to fill out the endpoint creation form:

**Field** | **Description** | **Recommended Value**
--- | --- | ---
Name | This unique value identifies the application that you require OAuth access for. | Microsoft Search
Client ID | A read-only, auto-generated unique ID for the application. The instance uses the client ID when it requests an access token. | NA
Client secret | With this shared secret string, the ServiceNow instance and Microsoft Search authorize communications with each other. | Follow security best-practices by treating this as a password.
Redirect URL | A required callback URL that the authorization server redirects to. | https://gcs.office.com/v1.0/admin/oauth/callback
Logo URL | A URL that contains the image for the application logo. | NA
Active | Select the check box to make the application registry active. | Set to active
Refresh token lifespan | The number of seconds that a refresh token is valid. By default, refresh tokens expire in 100 days (8640000 seconds). | 31,536,000 (1 year)
Access token lifespan | The number of seconds that an access token is valid. | 43,200 (12 hours)

Enter the client id and client secret to connect to your instance. After connecting, use a ServiceNow account credential to authenticate permission to crawl. The account should at least have **knowledge** role.

#### Azure AD OpenID Connect

To use Azure AD OpenID Connect for authentication, follow the steps below.

###### Step 1: Register a new application in Azure Active Directory

To learn about registering a new application in Azure Active Directory, see [Register an application](https://docs.microsoft.com/azure/active-directory/develop/quickstart-register-app#register-an-application). Select single tenant organizational directory. Redirect URI is not needed. After registration, note down the Application (client) ID and Directory (tenant) ID.

###### Step 2: Create a client secret

To learn about creating a client secret, see [Creating a client secret](https://docs.microsoft.com/azure/active-directory/develop/quickstart-register-app#add-a-client-secret). Take a note of client secret.

###### Step 3: Retrieve Service Principal Object Identifier

Follow the steps to retrieve Service Principal Object Identifier

1. Run PowerShell
2. Install Azure PowerShell using the following command
```<language>
   Install-Module -Name Az -AllowClobber -Scope CurrentUser
```
3. Connect to Azure
```<language>
    Connect-AzAccount
```
4. Get Service Principal Object Identifier
```<language>
   Get-AzADServicePrincipal -ApplicationId "Application-ID"
```
Replace "Application-ID" with Application (client) ID (without quotes) of the application you registered in step 1. Note the value of ID object from PowerShell output. It is the Service Principal ID.

Now you have all the information required from Azure portal. A quick summary of the information is given in the table below.

**Property** | **Description**
--- | ---
Directory ID (Tenant ID) | This is a unique ID referring the Azure Active Directory tenant (from step 1).
Application ID (Client ID) | This is a unique ID referring the application registered in step 1.
Client Secret | This is the secret key of the application (from step 2). Treat it like a password.
Service Principal ID | An identity for the application running as a service. (from step 3)

###### Step 4: Register ServiceNow Application

The following configuration need to be done in the ServiceNow instance.

1. Register a new OAuth OIDC entity. To learn, see [Create an OAuth OIDC provider](https://docs.servicenow.com/bundle/orlando-platform-administration/page/administer/security/task/add-OIDC-entity.html).
2. The following table provides guidance on how to fill out OIDC provider registration form

**Field** | **Description** | **Recommended Value**
--- | --- | ---
Name | A unique name that identifies the OAuth OIDC entity. | Azure AD
Client ID | The client ID of the application registered in the third-party OAuth OIDC server. The instance uses the client ID when requesting an access token. | Application (Client) ID from step 1
Client Secret | The client secret of the application registered in the third-party OAuth OIDC server. | Client Secret from step 2

All other values can be default.

3. In the OIDC provider registration form, you need to add a new OIDC provider configuration. Click the search icon against *OAuth OIDC Provider Configuration* field to open the records of OIDC configurations. Click New.
4. The following table provides guidance on how to fill out OIDC provider configuration form

**Field** | **Recommended Value**
--- | ---
OIDC Provider |  Azure AD
OIDC Metadata URL | This must be in the form https\://login.microsoftonline.com/"tenandId"/.well-known/openid-configuration <br/>Replace "tenantID" with Directory (tenant) ID from step 1 (without quotes).
OIDC Configuration Cache Life Span |  120
Application | Global
User Claim | sub
User Field | User ID
Enable JTI claim verification | Disabled

5. Click Submit and Update the OAuth OIDC Entity form.

###### Step 5: Create a ServiceNow account

Refer the instructions to create a ServiceNow account, [create a user in ServiceNow](https://docs.servicenow.com/bundle/paris-platform-administration/page/administer/users-and-groups/task/t_CreateAUser.html).

The following table provides guidance on how to fill out the ServiceNow user account registration

**Field** | **Recommended Value**
--- | ---
User ID | Service Principal ID from step 3
Web service access only | Checked

All other values can be left to default.

###### Step 6: Enable Knowledge role for the ServiceNow account

Access the ServiceNow account you created with ServiceNow Principal ID as User ID and assign the knowledge role. Instructions to assigning a role to a ServiceNow account can be found here, [assign a role to a user](https://docs.servicenow.com/bundle/paris-platform-administration/page/administer/users-and-groups/task/t_AssignARoleToAUser.html).

Use Application ID as Client ID (from step 1), and Client secret (from step 2) in admin center configuration wizard to authenticate to your ServiceNow instance using Azure AD OpenID Connect.

## Filter data

With a ServiceNow query string, you can specify conditions for syncing articles. It's like a **Where** clause in a **SQL Select** statement. For example, you can choose to index only articles that are published and active. To learn about creating your own query string, see [Generate an encoded query string using a filter](https://docs.servicenow.com/bundle/paris-platform-user-interface/page/use/using-lists/task/t_GenEncodQueryStringFilter.html).

## Manage search permissions

The ServiceNow connector supports search permissions visible to **Everyone** or **Only people with access to this data source**. Indexed data appears in the search results and is visible to all users in the organization or users who have access to them respectively. ServiceNow Connector supports default user criteria permissions without advanced scripts. When the connector encounters a user criteria with advanced script, all data using that user criteria will not be showed in search results.

If you choose **Only people with access to this data source**, you need to further choose whether your ServiceNow instance has Azure Active Directory (AAD) provisioned users or Non-AAD users.

>[!NOTE]
>If you choose AAD as the type of identity source, make sure you are assigning UPN source property to email targeted property in ServiceNow. To verify or change your mappings, see [Customizing user provisioning attribute-mappings for SaaS applications in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/app-provisioning/customize-application-attributes).

If you chose to ingest an ACL from your ServiceNow instance and selected "non-AAD" for the identity type see [Map your non-Azure AD Identities](map-non-aad.md) for instructions on mapping the identities.

## Manage the search schema

After successful connection, configure the search schema mapping. You can choose which properties to make **queryable**, **searchable**, and **retrievable**. To learn more about managing your search schema, see [Manage the search schema](https://docs.microsoft.com/microsoftsearch/configure-connector#manage-the-search-schema).

## Set the refresh schedule

The ServiceNow connector supports refresh schedules for both full and incremental crawls. We recommend that you set both.

A full crawl schedule finds deleted articles that were previously synced to the Microsoft Search index and any articles that moved out of the sync filter. When you first connect to ServiceNow, a full crawl runs to sync all the knowledge-base articles. To sync new items and make updates, you need to schedule incremental crawls.

The recommended default is one day for a full crawl and four hours for an incremental crawl.
>[!NOTE]
>For identities, only full crawl scheduled will be applied.

## Review and publish

After you configure your connector, you can review and publish the connection.

## Next steps

After publishing the connection, you need to customize the search results page. To learn about customizing search results, see [Customize the search results page](https://docs.microsoft.com/microsoftsearch/configure-connector#next-steps-customize-the-search-results-page).