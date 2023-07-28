---
title: "ServiceNow Catalog Microsoft Graph connector"
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
description: "Set up the ServiceNow Catalog Microsoft Graph connector for Microsoft Search"
---
<!---Previous ms.author: kam1 --->

# ServiceNow Catalog Microsoft Graph connector

With the Microsoft Graph connector for ServiceNow, your organization can list [service catalog](https://www.servicenow.com/products/it-service-automation-applications/service-catalog.html) items that are visible to all users or restricted with user criteria permissions within your organization. After you configure the connector and index content from ServiceNow, end users can search for those catalog items from any Microsoft Search client.

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors a ServiceNow Catalog Microsoft Graph  connector. It supplements the general instructions provided in the [Set up Microsoft Graph connectors in the Microsoft 365 admin center](configure-connector.md) article. If you haven't already done so, read the entire Set-up your Microsoft Graph connector article to understand the general setup process.

Each step in the setup process is listed below along with either a note that indicates you should follow the general setup instructions OR other instructions that apply only to ServiceNow connector including information about [Troubleshooting](#troubleshooting) and [Limitations](#limitations).

## Step 1: Add a connector in the Microsoft 365 admin center

Follow the general [setup instructions](./configure-connector.md).

## Step 2: Name the connection

Follow the general [setup instructions](./configure-connector.md).

## Step 3: Connection Settings

To connect to your ServiceNow data, you need your organization's **ServiceNow instance URL**. Your organization's ServiceNow instance URL typically looks like this: "**https://<span>&lt;your-organization-domain>.service-now.</span>com**".

Along with this URL, you'll need a **service account** for setting up the connection to ServiceNow and for allowing Microsoft Search to periodically update the catalog items based on the refresh schedule. The service account will need read access to the following **ServiceNow table records** to successfully crawl various entities.

Feature | Read access required tables | Description
--- | --- | ---
Index catalog items available to <em>Everyone</em> | sc_cat_item | For crawling catalog items
Index and support user criteria permissions | sc_cat_item_user_criteria_mtom | Who can access this catalog item
| | sc_cat_item_user_criteria_no_mtom | Who can't access this catalog item
| | sys_user | Read user table
| | sys_user_has_role | Read role information of users
| | sys_user_grmember | Read group membership of users
| | user_criteria | Read user criteria permissions

You can **create and assign a role** for the service account you use to connect with Microsoft Search. [Learn how to assign role for ServiceNow accounts](https://docs.servicenow.com/bundle/paris-platform-administration/page/administer/users-and-groups/task/t_AssignARoleToAUser.html). Read access to the tables can be assigned on the created role. To learn about setting read access to table records, see [Securing Table Records](https://developer.servicenow.com/dev.do#!/learn/learning-plans/orlando/new_to_servicenow/app_store_learnv2_securingapps_orlando_creating_and_editing_access_controls).

>[!NOTE]
> The ServiceNow Catalog connector can index catalog items and user criteria permissions without advanced scripts. If a user criteria contains advanced script all the related catalog items will be hidden from search results.

To authenticate and sync content from ServiceNow, choose **one of three** supported methods:

- Basic authentication
- ServiceNow OAuth (recommended)
- Azure Active Directory (Azure AD) OpenID Connect

## Step 3.1: Basic authentication

Enter the username and password of ServiceNow account with **catalog** role to authenticate to your instance.

## Step 3.2: ServiceNow OAuth

To use ServiceNow OAuth for authentication, a ServiceNow admin needs to provision an endpoint in your ServiceNow instance, so that the Microsoft Search app can access it. To learn more, see [Create an endpoint for clients to access the instance](https://docs.servicenow.com/bundle/newyork-platform-administration/page/administer/security/task/t_CreateEndpointforExternalClients.html) in the ServiceNow documentation.

The following table provides guidance on how to fill out the endpoint creation form:

Field | Description | Recommended Value
--- | --- | ---
Name | Unique value that identifies the application that you require OAuth access for. | Microsoft Search
Client ID | A read-only, auto generated unique ID for the application. The instance uses the client ID when it requests an access token. | N/A
Client secret | With this shared secret string, the ServiceNow instance and Microsoft Search authorize communications with each other. | Follow security best-practices by treating the secret as a password.
Redirect URL | A required callback URL that the authorization server redirects to. | For **M365 Enterprise**: https://<span>gcs.office.</span>com/v1.0/admin/oauth/callback,</br> For **M365 Government**: https://<span>gcsgcc.office.<span>com/v1.0/admin/oauth/callback
Logo URL | A URL that contains the image for the application logo. | N/A
Active | Select the check box to make the application registry active. | Set to active
Refresh token lifespan | The number of seconds that a refresh token is valid. By default, refresh tokens expire in 100 days (8,640,000 seconds). | 31,536,000 (one year)
Access token lifespan | The number of seconds that an access token is valid. | 43,200 (12 hours)

Enter the client ID and client secret to connect to your instance. After connecting, use a ServiceNow account credential to authenticate permission to crawl. The account should at least have **catalog** role. Refer to the table in the beginning of [step 3: connection settings](#step-3-connection-settings) for providing read access to more ServiceNow table records and index user criteria permissions.

## Step 3.3: Azure AD OpenID Connect

To use Azure AD OpenID Connect for authentication, follow the steps below.

### Step 3.3.1: Register a new application in Azure Active Directory

To learn about registering a new application in Azure Active Directory, see [Register an application](/azure/active-directory/develop/quickstart-register-app#register-an-application). Select single tenant organizational directory. Redirect URI isn't needed. After registration, note down the Application (client) ID and Directory (tenant) ID.

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

   Replace "Application-ID" with Application (client) ID (without quotes) of the application you registered in step 3.a. Note the value of ID object from PowerShell output. It's the Service Principal ID.

Now you have all the information required from Azure portal. A quick summary of the information is given in the table below.

Property | Description
--- | ---
Directory ID (Tenant ID) | Unique ID of the Azure Active Directory tenant, from step 3.a.
Application ID (Client ID) | Unique ID of the application registered in step 3.a.
Client Secret | The secret key of the application (from step 3.b). Treat it like a password.
Service Principal ID | An identity for the application running as a service. (from step 3.c)

### Step 3.3.4: Register ServiceNow Application

The ServiceNow instance needs the following configuration:

1. Register a new OAuth OIDC entity. To learn, see [Create an OAuth OIDC provider](https://docs.servicenow.com/bundle/orlando-platform-administration/page/administer/security/task/add-OIDC-entity.html).

2. The following table provides guidance on how to fill out OIDC provider registration form

   Field | Description | Recommended Value
   --- | --- | ---
   Name | A unique name that identifies the OAuth OIDC entity. | Azure AD
   Client ID | The client ID of the application registered in the third-party OAuth OIDC server. The instance uses the client ID when requesting an access token. | Application (Client) ID from step 3.a
   Client Secret | The client secret of the application registered in the third-party OAuth OIDC server. | Client Secret from step 3.b

   All other values can be default.

3. In the OIDC provider registration form, you need to add a new OIDC provider configuration. Select the search icon against *OAuth OIDC Provider Configuration* field to open the records of OIDC configurations. Select New.

4. The following table provides guidance on how to fill out OIDC provider configuration form

   Field | Recommended Value
   --- | ---
   OIDC Provider |  Azure AD
   OIDC Metadata URL | The URL must be in the form https\://login.microsoftonline.com/<tenandId">/.well-known/openid-configuration <br/>Replace "tenantID" with Directory (tenant) ID from step 3.a.
   OIDC Configuration Cache Life Span |  120
   Application | Global
   User Claim | sub
   User Field | User ID
   Enable JTI claim verification | Disabled

5. Select Submit and Update the OAuth OIDC Entity form.

### Step 3.3.5: Create a ServiceNow account

Refer the instructions to create a ServiceNow account, [create a user in ServiceNow](https://docs.servicenow.com/bundle/paris-platform-administration/page/administer/users-and-groups/task/t_CreateAUser.html).

The following table provides guidance on how to fill out the ServiceNow user account registration

Field | Recommended Value
--- | ---
User ID | Service Principal ID from step 3.c
Web service access only | Checked

All other values can be left to default.

### Step 3.3.6: Enable catalog role for the ServiceNow account

Access the ServiceNow account you created with ServiceNow Principal ID as User ID and assign the catalog role. Instructions to assigning a role to a ServiceNow account can be found here, [assign a role to a user](https://docs.servicenow.com/bundle/paris-platform-administration/page/administer/users-and-groups/task/t_AssignARoleToAUser.html). Refer to the table in the beginning of [step 3: connection settings](#step-3-connection-settings) for providing read access to more ServiceNow table records and index user criteria permissions.

Use Application ID as Client ID (from step 3.a), and Client secret (from step 3.b) in admin center configuration assistant to authenticate to your ServiceNow instance using Azure AD OpenID Connect.

## Step 4: Select properties and filter data

In this step, you can add or remove available properties from your ServiceNow data source. Microsoft 365 has already selected few properties by default.

With a ServiceNow query string, you can specify conditions for syncing articles. It's like a **Where** clause in a **SQL Select** statement. For example, you can choose to index only items that are active. To learn about creating your own query string, see [Generate an encoded query string using a filter](https://docs.servicenow.com/bundle/rome-platform-user-interface/page/use/using-lists/task/t_GenEncodQueryStringFilter.html).

Use the preview results button to verify the sample values of the selected properties and query filter.

## Step 5: Manage search permissions

The ServiceNow connector supports search permissions visible to **Everyone** or **Only people with access to this data source**. Indexed data appears in the search results and is visible to all users in the organization or users who have access to them via user criteria permission respectively. If a catalog item isn't enabled with a user criteria, it will appear in search results of everyone in the organization.

The connector supports default user criteria permissions without advanced scripts. When the connector encounters a user criteria with advanced script, all data using that user criteria won't appear in search results.

If you choose **Only people with access to this data source**, you need to further choose whether your ServiceNow instance has Azure Active Directory (Azure AD) provisioned users or Non-Azure AD users.

To identify which option is suitable for your organization:

1. Choose the **Azure AD** option if the Email ID of ServiceNow users is **same** as the UserPrincipalName (UPN) of users in Azure AD.
2. Choose the **Non-Azure AD** option if the email ID of ServiceNow users is **different** from the UserPrincipalName (UPN) of users in Azure AD.

>[!NOTE]
>
> - If you choose Azure AD as the type of identity source, the connector maps the Email IDs of users obtained from ServiceNow directly to UPN property from Azure AD.
> - If you chose "Non-Azure AD" for the identity type see [Map your non-Azure AD Identities](./map-non-aad.md) for instructions on mapping the identities. You can use this option to provide the mapping regular expression from Email ID to UPN.

## Step 6: Assign property labels

Follow the general [setup instructions](./configure-connector.md).

## Step 7: Manage schema

Follow the general [setup instructions](./configure-connector.md).

## Step 8: Choose refresh settings

Follow the general [setup instructions](./configure-connector.md).

>[!NOTE]
>For identities, only full crawl scheduled will be applied.

## Step 9: Review Connection

Follow the general [setup instructions](./configure-connector.md).

After publishing the connection, you need to customize the search results page. To learn about customizing search results, see [Customize the search results page](/microsoftsearch/configure-connector#next-steps-customize-the-search-results-page).

## Limitations

ServiceNow Catalog Microsoft Graph connector has the following limitations in its latest release:

- *Only people with access to this data source* feature under Manage Search permissions step processes only [user criteria](https://hi.service-now.com/kb_view.do?sysparm_article=KB0550924) permissions. Any other type of access permissions won't be applied in the search results.
- User criteria permissions configured at catalog category aren't supported.
- User criteria with advanced scripts aren't supported in the current version. Any catalog items with such an access restriction will be indexed with deny everyone access that is, they won't appear in search results to any user until we support them.

## Troubleshooting

After publishing your connection, customizing the results page, you can review the status under the **Data Sources** tab in the [admin center](https://admin.microsoft.com). To learn how to make updates and deletions, see [Manage your connector](manage-connector.md).
You can find troubleshooting steps for commonly seen issues below.

### 1. Unable to sign in due to Single Sign-on enabled ServiceNow instance

If your organization has enabled Single Sign-on (SSO) to ServiceNow, you may have trouble logging in with the service account. You can bring up username and password based sign-in by adding <em> `login.do`</em> to the ServiceNow instance URL. Example: `https://<your-organization-domain>.service-now.com./login.do`.

### 2. Unauthorized or forbidden response to API request

#### 2.1. Check table access permissions

If you see forbidden or unauthorized response in connection status, check if the service account has required access to the tables mentioned in [step 3: connection settings](#step-3-connection-settings). Check whether all the columns in the tables have read access.

#### 2.2. Change in account password

The connector uses access token fetched on behalf of service account for crawl. The access token refreshes every 12 hours. Ensure that service account password isn't changed after publishing the connection. You may need to reauthenticate the connection if there's a change in password.

#### 2.3. Check if ServiceNow instance behind firewall

Your Microsoft Graph connector may not be able to reach your ServiceNow instance if it is behind a network firewall. You'll need to explicitly allow access to connector service. You can find public IP address range of the connector service in the table below. Based on your tenant region, add it to your ServiceNow instance network allowlist.

 Environment | Region | Range
--- | --- | ---
PROD | North America | 52.250.92.252/30, 52.224.250.216/30
PROD | Europe | 20.54.41.208/30, 51.105.159.88/30
PROD | Asia Pacific | 52.139.188.212/30, 20.43.146.44/30

#### 2.4. Access permissions not working as expected

If you observe discrepancies in access permissions applied to search results, verify user criteria configuration in [applying user criteria to catalog items](https://docs.servicenow.com/bundle/orlando-it-service-management/page/product/service-catalog-management/task/t_AppUserCritItemsCat.html).

### 3. Issues with *Only people with access to this data source* permission

#### 3.1 Unable to choose *Only people with access to this data source*

You may not be able to choose *Only people with access to this data source* option if the service account doesn't have read permissions to the required tables in [step 3: connection settings](#step-3-connection-settings). Check whether the service account can read tables mentioned under *Index and support user criteria permissions* feature.

#### 3.2 User mapping failures

 ServiceNow user accounts that don't have a Microsoft 365 user in Azure Active Directory won't map. Non-user, service accounts are expected to fail user mapping. Number of user mapping failures can be accessed in identity stats area in connection detail window. Log of failed user mappings can be downloaded from Error tab.

### 4. Issues with user criteria access flow

If you see differences in the user criteria validation between ServiceNow and Microsoft Search, set `glide.knowman.block_access_with_no_user_criteria` system property to `no`.

If you have any other issues or want to provide feedback, write to us [aka.ms/TalkToGraphConnectors](https://aka.ms/TalkToGraphConnectors)
