---
ms.date: 10/08/2019
title: "ServiceNow Tickets Microsoft Graph connector"
ms.author: kam1
author: TheKarthikeyan
manager: harshkum
audience: Admin
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
description: "Set up the ServiceNow Tickets Microsoft Graph connector for Microsoft Search"
---
<!---Previous ms.author: kam1 --->

# ServiceNow Tickets Microsoft Graph connector

With the ServiceNow Tickets Microsoft Graph connector, your organization can index various tickets that are serviced to users. After you configure the connector and index content from ServiceNow, end users can search for those tickets from any Microsoft Search client.  

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors a ServiceNow Tickets Graph connector. It supplements the general instructions provided in the [Set up Microsoft Graph connectors in the Microsoft 365 admin center](configure-connector.md) article. If you haven't already done so, read the entire 'Setup your ServiceNow Tickets Microsoft Graph connector' article to understand the general setup process.

Each step in the setup process is listed below along with either a note that indicates you should follow the general setup instructions OR 
other instructions that apply to only ServiceNow connector including information about [Troubleshooting](#troubleshooting). 
and [Limitations](#limitations).  

## Step 1: Add a connector in the Microsoft 365 admin center.

[Add ServiceNow Tickets connector](https://admin.microsoft.com/adminportal/home#/MicrosoftSearch/Connectors/add?ms_search_referrer=MicrosoftSearchDocs_ServiceNowTickets&type=ServiceNowTickets​)

Follow the general [setup instructions](./configure-connector.md).

## Step 2: Name the connection.
Follow the general [setup instructions](./configure-connector.md).

## Step 3: Connection settings
To connect to your ServiceNow data, you need your organization's **ServiceNow instance URL**. Your organization's ServiceNow instance URL typically looks like **https://&lt;your-organization-domain>.service-now.com**. 

Along with this URL, you'll need a **service account** for setting up the connection to ServiceNow and for allowing Microsoft Search to periodically update the ticket details based on the refresh schedule. 

In ServiceNow, the task table is the base class for ticket management. It can be extended to create ticket applications such as incident, problem and change management. Learn more about [ServiceNow Task tables](https://docs.servicenow.com/bundle/washingtondc-platform-administration/page/administer/task-table/concept/c_TaskTable.html).

The service account you use to configure a connection **must have** read access to the following ServiceNow table records to successfully crawl default ticket fields.

**Feature** | **Read access required tables** | **Description**
--- | --- | ---
Index base [Task table fields](https://docs.servicenow.com/bundle/sandiego-platform-administration/page/administer/task-table/reference/r_ImportantTaskTableFields.html#r_ImportantTaskTableFields) | `task` | For crawling default fields from out of the box task tables
Sync user tables | `sys_user` | To index user access details for tickets


If you want to index custom properties from [extended tables](https://docs.servicenow.com/bundle/washingtondc-application-development/page/administer/table-administration/concept/table-extension-and-classes.html) of *task* table, provide read access to sys_dictionary and sys_db_object. 
It is an **optional** feature. You'll be able to index *task* table properties without access to the two extra tables.

**Feature** | **Read access required tables** | **Description**
--- | --- | ---
Select a custom table from your organization| `sys_db_object` | Find the list of extended task tables including custom tables
Index custom fields from a specific <table_name> | `sys_dictionary` | Crawling custom fields from a specific table like incident, problem or change_management

You can **create and assign a role** for the service account you use to connect with Microsoft Search. [Learn how to assign role for ServiceNow accounts](https://docs.servicenow.com/bundle/washingtondc-platform-administration/page/administer/users-and-groups/task/t_AssignARoleToAUser.html). Read access to the tables can be provided to the created role. To learn about setting read access to table records, see [Securing Table Records](https://developer.servicenow.com/dev.do#!/learn/learning-plans/sandiego/new_to_servicenow/app_store_learnv2_securingapps_sandiego_securing_table_records). 


To authenticate and sync content from ServiceNow, choose **one of three** supported methods:

- Basic authentication
- ServiceNow OAuth (recommended)
- Microsoft Entra ID OpenID Connect

## Step 3.1: Basic authentication

Enter the username and password of the ServiceNow account with read access to the `task` and `sys_user` tables to authenticate to your instance.

## Step 3.2: ServiceNow OAuth

To use ServiceNow OAuth, a ServiceNow admin needs to provision an endpoint in your ServiceNow instance. After that Microsoft Search app will be able to access it. To learn more, see [Create an endpoint for clients to access the instance](https://docs.servicenow.com/bundle/washingtondc-platform-security/page/administer/security/task/t_CreateEndpointforExternalClients.html) in the ServiceNow documentation.

The following table provides guidance on how to fill out the endpoint creation form:

Field | Description | Recommended Value
--- | --- | ---
Name | Unique value that identifies the application that you require OAuth access to. | Microsoft Search
Client ID | A read-only, auto-generated unique ID for the application. The instance uses the client ID when it requests an access token. | NA
Client secret | With this shared secret string, the ServiceNow instance and Microsoft Search authorize communications with each other. | Follow security best practices by treating the secret as a password.
Redirect URL | A required callback URL that the authorization server redirects to. | `https://gcs.office.com/v1.0/admin/oauth/callback`
Logo URL | A URL that contains the image for the application logo. | NA
Active | Select the check box to make the application registry active. | Set to active
Refresh token lifespan | The number of seconds that a refresh token is valid. By default, refresh tokens expire in 100 days (8,640,000 seconds). | 31,536,000 (one year)
Access token lifespan | The number of seconds that an access token is valid. | 43,200 (12 hours)

Enter the client ID and client secret to connect to your instance. After connecting, use a ServiceNow account credential to authenticate permission to crawl. The account should at least have read access to `task` and `sys_user` tables. Refer to the table at the beginning of [step 3: connection settings](#step-3-connection-settings) for providing read access to more ServiceNow table records and index user criteria permissions.

<a name='step-33-azure-ad-openid-connect'></a>

## Step 3.3: Microsoft Entra ID OpenID Connect

To use Microsoft Entra ID OpenID Connect for authentication, follow the steps below.

<a name='step-331-register-a-new-application-in-azure-active-directory'></a>

### Step 3.3.1: Register a new application in Microsoft Entra ID

To learn about registering a new application in Microsoft Entra ID, see [Register an application](/azure/active-directory/develop/quickstart-register-app#register-an-application). Select single tenant organizational directory. Redirect URI isn't needed. After registration, note down the Application (client) ID and Directory ID (Tenant ID).

### Step 3.3.2: Create a client secret

To learn about creating a client secret, see [Creating a client secret](/azure/active-directory/develop/quickstart-register-app#add-a-client-secret). Take a note of client secret.

### Step 3.3.3: Retrieve Service Principal Object Identifier

Follow the steps to retrieve Service Principal Object Identifier

1. Run PowerShell.

2. Install Azure PowerShell using the following command.

   ```powershell
   Install-Module -Name Az -AllowClobber -Scope CurrentUser
   ```

3. Connect to Azure.

   ```powershell
   Connect-AzAccount
   ```

4. Get Service Principal Object Identifier.

   ```powershell
   Get-AzADServicePrincipal -ApplicationId "Application-ID"
   ```
   Replace "Application-ID" with the Application (client) ID (without quotes) of the application you registered in step 3.a. Note the value of ID object from PowerShell output. It's the Service Principal ID.

Now you have all the information required from the Azure portal. A quick summary of the information is given in the table below.

Property | Description
--- | ---
Directory ID (Tenant ID) | Unique ID of the Microsoft Entra tenant, from step 3.a.
Application ID (Client ID) | Unique ID of the application registered in step 3.a.
Client Secret | The secret key of the application (from step 3.b). Treat it like a password.
Service Principal ID | An identity for the application running as a service. (from step 3.c)

### Step 3.3.4: Register ServiceNow Application

The ServiceNow instance needs the following configuration:

1. Register a new OAuth OIDC entity. To learn, see [Create an OAuth OIDC provider](https://docs.servicenow.com/bundle/washingtondc-platform-security/page/administer/security/task/add-OIDC-entity.html).

2. The following table provides guidance on how to fill out OIDC provider registration form

   Field | Description | Recommended Value
   --- | --- | ---
   Name | A unique name that identifies the OAuth OIDC entity. | Microsoft Entra ID
   Client ID | The client ID of the application registered in the third-party OAuth OIDC server. The instance uses the client ID when requesting an access token. | Application (Client) ID from step 3.a
   Client Secret | The client secret of the application registered in the third-party OAuth OIDC server. | Client Secret from step 3.b

   All other values can be default.

3. In the OIDC provider registration form, you need to add a new OIDC provider configuration. Select the search icon against *OAuth OIDC Provider Configuration* field to open the records of OIDC configurations. Select New.

4. The following table provides guidance on how to fill out OIDC provider configuration form

   Field | Recommended Value
   --- | ---
   OIDC Provider |  Microsoft Entra ID
   OIDC Metadata URL | The URL must be in the form https\://login.microsoftonline.com/<tenandId">/.well-known/openid-configuration <br/>Replace "tenantID" with Directory ID (Tenant ID) from step 3.a.
   OIDC Configuration Cache Life Span |  120
   Application | Global
   User Claim | sub
   User Field | User ID
   Enable JTI claim verification | Disabled

5. Select Submit and Update the OAuth OIDC Entity form.

### Step 3.3.5: Create a ServiceNow account

Refer the instructions to create a ServiceNow account, [create a user in ServiceNow](https://docs.servicenow.com/bundle/washingtondc-platform-administration/page/administer/users-and-groups/task/t_CreateAUser.html).

The following table provides guidance on how to fill out the ServiceNow user account registration

Field | Recommended Value
--- | ---
User ID | Service Principal ID from step 3.c
Web service access only | Checked

All other values can be left to default.

### Step 3.3.6: Enable Task, User table access for the ServiceNow account

Access the ServiceNow account you created with ServiceNow Principal ID as User ID and assign the read access to `task` and `sys_user` table. Refer to the table at the beginning of [step 3: connection settings](#step-3-connection-settings) for providing read access to more ServiceNow table records and index custom fields.

Use Application ID as Client ID (from step 3.a), and Client secret (from step 3.b) in the M365 admin center configuration window to authenticate to your ServiceNow instance using Microsoft Entra ID OpenID Connect.

## Step 4: Select tables, properties, and filter data

In this step, you can add or remove available tables and properties from your ServiceNow data source. Microsoft 365 has already selected a few tables and properties by default.

*The list of properties that you select here, can impact how can you filter, search, and view your results in Microsoft 365 Copilot.*

**Source property** | **Label** | **Description**
--- | --- | ---
AccessUrl  | `url` | The target URL of the item in the data source.
IconUrl   | `iconUrl` | Icon url that represents the article’s category or type.
OpenedBy   | `authors` | Name of people who participated/collaborated on the item in the data source.
ShortDescription   | `title` | The title of the item that you want to be shown in search and other experiences.
SysCreatedBy   | `createdBy` | Name of the person who created the item in the data source.
SysCreatedOn   | `createdDateTime` | Date and time that the item was created in the data source.
SysUpdatedBy   | `lastModifiedBy` | Name of the person who most recently edited the item in the data source.
SysUpdatedOn  | `lastModifiedDateTime` | Date and time the item was last modified in the data source.

With a ServiceNow query string, you can specify conditions for syncing tickets. It's like a **Where** clause in a **SQL Select** statement. For example, you can choose to index only tickets that are created in the last six months and are in open state. To learn about creating your own query string, see [Generate an encoded query string using a filter](https://docs.servicenow.com/bundle/washingtondc-platform-user-interface/page/use/using-lists/task/t_GenEncodQueryStringFilter.html).

Use the preview results button to verify the sample values of the selected properties and query filter.

## Step 5: Manage search permissions

The ServiceNow Tickets Microsoft Graph connector supports search permissions visible to **Only people with access to this data source**. Indexed tickets appear in the search results and are visible to users who have access to them via `assigned_to` and `opened_by` fields.

When you choose **Only people with access to this data source**, you need to further choose whether your ServiceNow instance has Microsoft Entra ID provisioned users or non-Azure AD users.

To identify which option is suitable for your organization:

1. Choose the **Microsoft Entra ID** option if the email ID of ServiceNow users is **same** as the UserPrincipalName (UPN) of users in Microsoft Entra ID.
2. Choose the **Non-Azure AD** option if the email ID of ServiceNow users is **different** from the UserPrincipalName (UPN) of users in Microsoft Entra ID. 

>[!NOTE]
> * If you choose Microsoft Entra ID as the type of identity source, the connector maps the email IDs of users obtained from ServiceNow directly to UPN property from Microsoft Entra ID.
> * If you chose "Non-Azure AD" for the identity type see [Map your non-Azure AD Identities](map-non-aad.md) for instructions on mapping the identities. You can use this option to provide the mapping regular expression from email ID to UPN.
> * Updates to users or groups governing access permissions are synced in full crawls only. Incremental crawls do not currently support the processing of updates to permissions.

## Step 6: Assign property labels

Follow the general [setup instructions](./configure-connector.md).

## Step 7: Manage schema

Follow the general [setup instructions](./configure-connector.md).

## Step 8: Choose refresh settings

Follow the general [setup instructions](./configure-connector.md).

>[!NOTE]
>For identities, only the full crawl schedule is applied.

## Step 9: Review Connection

Follow the general [setup instructions](./configure-connector.md).

After publishing the connection, you need to customize the search results page. To learn about customizing search results, see [Customize the search results page](/microsoftsearch/configure-connector#next-steps-customize-the-search-results-page).

## Limitations
The ServiceNow Tickets Microsoft Graph connector has the following limitations in its latest release:

- *Everyone* feature under the Manage Search permissions step doesn't process any permissions. Don't select this option unless you want to test the connection between selected team members in an isolated environment.

## Troubleshooting
After publishing your connection, and customizing the results page, you can review the status under the **Data Sources** tab in the [admin center](https://admin.microsoft.com). To learn how to make updates and deletions, see [Manage your connector](manage-connector.md).
You can find troubleshooting steps for commonly seen issues [here](troubleshoot-servicenow-tickets-connector.md).
