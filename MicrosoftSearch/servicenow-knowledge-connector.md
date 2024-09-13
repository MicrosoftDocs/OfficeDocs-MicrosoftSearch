---
ms.date: 05/09/2024
title: "ServiceNow Knowledge Microsoft Graph connector"
ms.author: souravpoddar
author: souravpoddar001
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
description: "Set up the ServiceNow Knowledge Microsoft Graph connector for Microsoft Search and Microsoft 365 Copilot."
---
# ServiceNow Knowledge Microsoft Graph connector

With the ServiceNow Knowledge Microsoft Graph connector, your organization can index knowledge-base articles that are visible to all users or restricted with user criteria permissions within your organization. After you configure the connector and index content from ServiceNow, end users can search for those articles in Microsoft 365 Copilot and from any Microsoft Search client.  

You can also refer to [this video](https://www.youtube.com/watch?v=TVSkJpk1RiE) to learn more about the Microsoft Graph connector's capability in managing search permissions.

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors a ServiceNow Knowledge Microsoft Graph connector. It supplements the general instructions provided in the [Set up Microsoft Graph connectors in the Microsoft 365 admin center](configure-connector.md) article. 

Each step in the setup process is listed below along with either a note that indicates you should follow the general setup instructions OR other instructions that apply to only ServiceNow Knowledge Microsoft Graph connector including information about [Troubleshooting](#troubleshooting) and [Limitations](#limitations).

## Mandatory and optional settings
To get you quickly started with Microsoft Graph connectors, the steps in the setup process are split into two groups:

**Mandatory settings** - You must provide some input for these steps to make the connection. The inputs (connection name, data source settings, etc.) vary based on your organization's context and use case.

**Advanced settings (optional)** - As the name suggests, Advanced settings are optional steps. For your convenience, these settings in the setup process are preconfigured with default values based on the most common selections made by admins. You can choose to accept the default values or modify them to suit your organization's needs.

## Get started

[Add the ServiceNow Knowledge Microsoft Graph connector](https://admin.microsoft.com/adminportal/home#/MicrosoftSearch/Connectors/add?ms_search_referrer=MicrosoftSearchDocs_ServiceNowKB&type=ServiceNowKB)

(For more details, see general [setup instructions](./configure-connector.md))

## Mandatory settings

   ### 1. Name & ID:
   **Connection ID**: Edit the connection ID  if necessary (prefilled with a default and unique string). You can't edit it after you click on the **'Save and proceed'** button.
    
   **Name**: Enter a name for your connection (prefilled with a default name). You can always edit it later (even after the connection is published).
 
   :::image type="content" alt-text="Screenshot of the Name & ID fields." source="media/servicenow-knowledge-connector-name-and-id.png" lightbox="media/servicenow-knowledge-connector-name-and-id.png":::

   ### 2. Data source settings:

   **ServiceNow instance URL**: To connect to your ServiceNow data, you need your organization's **ServiceNow instance URL**. Your organization's ServiceNow instance URL typically looks like **https://&lt;your-organization-domain>.service-now.com**. 

   :::image type="content" alt-text="Screenshot of the Data Source Settings." source="media/servicenow-knowledge-connector-data-source-settings.png" lightbox="media/servicenow-knowledge-connector-data-source-settings.png":::

   Along with this URL, you need a **Service account** for setting up the connection to ServiceNow and to allow Microsoft Search and Microsoft 365 Copilot to periodically update the knowledge articles based on the refresh schedule. The service account needs read access to the following **ServiceNow table records** to successfully crawl various entities.

   |Feature | Read access required tables | Description
   |:---|:---|:---|
   |Index knowledge articles available to <em>Everyone</em> | kb_knowledge | For crawling knowledge articles.|
   |Index and support user criteria permissions | kb_uc_can_read_mtom | Who can read this knowledge base.|
   | | kb_uc_can_contribute_mtom | Who can contribute to this knowledge base.|
   | | kb_uc_cannot_read_mtom | Who cannot read this knowledge base.|
   | | kb_uc_cannot_contribute_mtom | Who cannot contribute to this knowledge base.|
   | | sys_user | Read user table.|
   | | sys_user_has_role | Read role information of users.|
   | | sys_user_grmember | Read group membership of users.|
   | | user_criteria | Read user criteria permissions.|
   | | kb_knowledge_base | Read knowledge base information.|
   | | sys_user_group | Read user group segments.|
   | | sys_user_role | Read user roles.|
   | | cmn_location | Read location information.|
   | | cmn_department | Read department information.|
   | | core_company | Read company attributes.|
   Index extended table properties (optional) | sys_db_object | Read extended table details.|
   | | sys_dictionary | Read extended table properties.|

You can **create and assign a role** for the service account you use to connect with Microsoft Search and Microsoft 365 Copilot. For more information, see [Learn how to assign role for ServiceNow accounts](https://docs.servicenow.com/bundle/vancouver-platform-administration/page/administer/users-and-groups/task/t_AssignARoleToAUser.html). 
Read access to tables can be assigned on the created role. For more information, see [Securing table records](https://developer.servicenow.com/dev.do#!/learn/learning-plans/vancouver/new_to_servicenow/app_store_learnv2_securingapps_vancouver_creating_and_editing_access_controls). 

If you want to index properties from [extended tables](https://docs.servicenow.com/bundle/vancouver-platform-administration/page/administer/table-administration/concept/table-extension-and-classes.html) of *kb_knowledge*, provide read access to sys_dictionary and sys_db_object. This is an optional feature. You can index *kb_knowledge* table properties without access to the two additional tables.

   >[!NOTE]
   > The ServiceNow Knowledge Microsoft Graph connector can index knowledge articles and user criteria permissions without advanced scripts. For more information, see [Read and deny access to knowledge articles in the ServiceNow Knowledge Microsoft Graph connector](#read-and-deny-access-to-knowledge-articles-in-microsoft-graph-connector-for-servicenow).

 **Authentication details**: To authenticate and sync content from ServiceNow, choose **one of three** supported methods:
   - [Basic authentication](#1-basic-authentication)
   - [ServiceNow OAuth (recommended)](#2-servicenow-oauth)
   - [Microsoft Entra ID OpenID Connect](#3-microsoft-entra-id-openid-connect)

   a. **Basic authentication** <br>
     Enter the username and password of ServiceNow account with **knowledge** role to authenticate to your instance.
     <br>

   b. **ServiceNow OAuth (Recommended)**
   <details>
   <summary>[Click to expand]To use the ServiceNow OAuth for authentication, follow these steps.</summary><br>
    
   A ServiceNow admin needs to provision an endpoint in your ServiceNow instance, so that the Graph connector can access it. To learn more, see [Create an endpoint for clients to access the instance](https://docs.servicenow.com/bundle/vancouver-platform-security/page/administer/security/task/t_CreateEndpointforExternalClients.html) in the ServiceNow documentation.

   The following table provides guidance on how to fill out the endpoint creation form:

   |Field | Description | Recommended value
   |:--- |:--- |:---   
   Name | Unique value that identifies the application that you require OAuth access for. | Microsoft Search
   Client ID | A read-only, auto generated unique ID for the application. The instance uses the client ID when it requests an access token. | NA
   Client secret | With this shared secret string, the ServiceNow instance and Microsoft Search authorize communications with each other. | Follow security best-practices by treating the secret as a password.
   Redirect URL | A required callback URL that the authorization server redirects to. | For **M365 Enterprise**: https://<span>gcs.office.</span>com/v1.0/admin/oauth/callback,</br> For **M365 Government**: https://<span>gcsgcc.office.<span>com/v1.0/admin/oauth/callback
   Logo URL | A URL that contains the image for the application logo. | NA
   Active | Select the check box to make the application registry active. | Set to active
   Refresh token lifespan | The number of seconds that a refresh token is valid. By default, refresh tokens expire in 100 days (8,640,000 seconds). | 31,536,000 (one year)
   Access token lifespan | The number of seconds that an access token is valid. | 43,200 (12 hours)
   
   Enter the client id and client secret to connect to your instance. After connecting, use a ServiceNow account credential to authenticate permission to crawl. The account should at least have **knowledge** role. Refer to the table mentioned under Service account in the [Prerequisites](#prerequisites) section for providing read access to more ServiceNow table records and index user criteria permissions.
</details> <br>

   c. **Microsoft Entra ID OpenID Connect**

   <details>

   <summary>To use Microsoft Entra ID OpenID Connect for authentication, follow the steps below.</summary>

   <a name='step-331-register-a-new-application-in-azure-active-directory'></a>

   1. Register a new application in Microsoft Entra ID

      To learn about registering a new application in Microsoft Entra ID, see [Register an application](/azure/active-directory/develop/quickstart-register-app#register-an-application). Select single tenant organizational directory. Redirect URI isn't needed. After registration, note down the Application (client) ID and Directory (tenant) ID.

   2. Create a client secret

      To learn about creating a client secret, see [Creating a client secret](/azure/active-directory/develop/quickstart-register-app#add-a-client-secret). Take a note of client secret.

   3. Retrieve service principal object identifier

         Follow the steps to retrieve service principal object identifier

         1. Run PowerShell.

         1. Install Azure PowerShell using the following command.

            ```powershell
            Install-Module -Name Az -AllowClobber -Scope CurrentUser
            ```

         1. Connect to Azure.

             ```powershell
             Connect-AzAccount
             ```

         1. Get Service Principal Object Identifier.

             ```powershell
             Get-AzADServicePrincipal -ApplicationId "Application-ID"
             ```
  
             Replace "Application-ID" with Application (client) ID (without quotes) of the application you registered in step 1. Note the value of the ID object from PowerShell output. It's the Service Principal ID.

            Now you have all the information required from Azure portal. A quick summary of the information is given in the table below.

         |Property | Description
         |:--- |:---|
         |Directory ID (tenant ID) | Unique ID of the Microsoft Entra tenant, from step 3.a.|
         |Application ID (client ID) | Unique ID of the application registered in step 3.a.|
         |Client secret | The secret key of the application (from step 3.b). Treat it like a password.|
         |Service principal ID | An identity for the application running as a service. (from step 3.c)|

      4. Register the ServiceNow application

      The ServiceNow instance needs the following configuration:

         1. Register a new OAuth OIDC entity. To learn, see [Create an OAuth OIDC provider](https://docs.servicenow.com/bundle/vancouver-platform-security/page/administer/security/task/add-OIDC-entity.html).

         1. The following table provides guidance on how to fill out OIDC provider registration form

              |Field | Description | Recommended value
              |:--- |:---|:---|
              |Name | A unique name that identifies the OAuth OIDC entity. | Microsoft Entra ID|
              |Client ID | The client ID of the application registered in the third-party OAuth OIDC server. The instance uses the client ID when requesting an access token. | Application (client) ID from step 3.a|
              |Client secret | The client secret of the application registered in the third-party OAuth OIDC server. | Client secret from step 3.b|

            All other values can be default.

         1. In the OIDC provider registration form, you need to add a new OIDC provider configuration. Select the search icon against *OAuth OIDC Provider Configuration* field to open the records of OIDC configurations. Select New.

         1. The following table provides guidance on how to fill out OIDC provider configuration form

             |Field | Recommended value
             |:--- |:---|
             |OIDC provider |  Microsoft Entra ID|
             |OIDC Metadata URL | The URL must be in the form https\://login.microsoftonline.com/<tenandId">/.well-known/openid-configuration <br/>Replace "tenantID" with Directory (tenant) ID from step 3.a.|
             |OIDC configuration cache life span |  120|
             |Application | Global|
             |User claim | sub|
             |User field | User ID|
             |Enable JTI claim verification | Disabled|

          1. Select Submit and update the OAuth OIDC entity form.

   5. Create a ServiceNow account

      Refer to the instructions to create a ServiceNow account, [create a user in ServiceNow](https://docs.servicenow.com/bundle/vancouver-platform-administration/page/administer/users-and-groups/task/t_CreateAUser.html).

     The following table provides guidance on how to fill out the ServiceNow user account registration

      |Field | Recommended value
      |:--- |:---|
      |User ID | Service Principal ID from step 3.c|
      |Web service access only | Checked|

      All other values can be left to default.

   6. Enable Knowledge role for the ServiceNow account

      Access the ServiceNow account you created with ServiceNow Principal ID as User ID and assign the knowledge role. Instructions to assigning a role to a ServiceNow account can be found here, [assign a role to a user](https://docs.servicenow.com/bundle/vancouver-platform-administration/page/administer/users-and-groups/task/t_AssignARoleToAUser.html). Refer to the table mentioned under Service account in the [Prerequisites](#prerequisites) section for providing read access to more ServiceNow table records and index user criteria permissions.

      Use Application ID as client ID (from step 3.1), and client secret (from step 3.2) in the admin center configuration wizard to authenticate to your ServiceNow instance using Microsoft Entra ID OpenID Connect.
</details>
### 3. Access permissions
               
The ServiceNow Knowledge Microsoft Graph connector supports access permissions visible to **Everyone** or **Only people with access to this data source**. Indexed data appears in the search results and is visible to all users in the organization or users who have access to them via user criteria permission respectively. If a knowledge article isn't enabled with user criteria, it appears in the search results of everyone in the organization.

:::image type="content" alt-text="Screenshot that shows access permissions." source="media/servicenow-knowledge-connector-access-permissions.png" lightbox="media/servicenow-knowledge-connector-access-permissions.png":::

>[!IMPORTANT]
>In ServiceNow, while assessing read permissions for a user, both article-level permissions and KB-level permissions are looked at. The ServiceNow Knowledge Microsoft Graph connector treats permissions differently:
>1. If the article contains '_Can Read_' user criteria, then they are stamped on the article during ingestion, and Knowledge Base '_Can Read_' / '_Can Contribute_' user criteria are ignored.
>2. If the article contains '_Cannot Read_' user criteria, and if the corresponding Knowledge base also contains '_Cannot Read_' user criteria, then both the user criteria are stamped on the article.

>**Note**: If a user is part of the '_Can Read_' user criteria at the article level but not in the '_Can Read_' / '_Can Contribute_' user criteria at the Knowledge base level, **then the user will not have access to the article in ServiceNow but will have access to the article in Microsoft 365 Copilot, Microsoft Search, and other Microsoft 365 surfaces**. The workaround is to remove the user from the '_Can Read_' user criteria at the article level.

If you choose **Only people with access to this data source**, you need to further choose whether your ServiceNow instance has Microsoft Entra ID provisioned users or non-AAD users.

To identify which option is suitable for your organization:
               
1. Choose the **Microsoft Entra ID** option if the email ID of ServiceNow users is **same** as the UserPrincipalName (UPN) of users in Microsoft Entra ID.
2. Choose the **non-AAD** option if the email ID of ServiceNow users is **different** from the UserPrincipalName (UPN) of users in Microsoft Entra ID. 

## Advanced settings (optional)
               
### 1. Select properties

In this step, you can add or remove available properties from your ServiceNow data source. Microsoft 365 selects a few properties by default.

[![Screenshot that shows Content tab where you can configure Query string and Properties.](/MicrosoftSearch/media/servicenow-knowledge-content-tab.png)](/MicrosoftSearch/media/servicenow-knowledge-content-tab.png#lightbox)

The list of properties that you select here, can impact how can you filter, search, and view your results in Microsoft 365 Copilot.

|Source property|Label|Description
|:---|:---|:---|
|AccessUrl  | `url` | The target URL of the item in the data source.|
|Author   | `authors` | Name of all the people who participated/collaborated on the item in the data source.|
|IconUrl   | `iconUrl` | Icon url that represents the article’s category or type.|
|Short_description  | `title` | The title of the item that you want to be shown in search and other experiences.|
|SysUpdatedBy   | `lastModifiedBy` | Name of the person who most recently edited the item in the data source.|
|SysUpdatedOn  | `lastModifiedDateTime` | Date and time the item was last modified in the data source.|
|SysCreatedBy   | `createdBy` | Name of the person who created the item in the data source.|
|SysCreatedOn   | `createdDateTime` | Date and time that the item was created in the data source.|

With a ServiceNow query string, you can specify conditions for syncing articles. It's like a **Where** clause in a **SQL Select** statement. For example, you can choose to index only articles that are published and active. To learn about creating your own query string, see [Generate an encoded query string using a filter](https://docs.servicenow.com/bundle/vancouver-platform-user-interface/page/use/using-lists/task/t_GenEncodQueryStringFilter.html).

Use the preview results button to verify the sample values of the selected properties and query filter.

### 2. Map identities

In this step, you can map identities for both Microsoft Entra ID and Non-Microsoft Entra ID identity types.

* If you choose Microsoft Entra ID as the type of identity source, the connector maps the email IDs of users obtained from ServiceNow directly to UPN property from Microsoft Entra ID.
* If you choose "non-AAD" for the identity type see [Map your non-Azure AD Identities](map-non-aad.md) for instructions on mapping the identities.


### 3. Assign property labels

Follow the general [setup instructions](./configure-connector.md#step-6-assign-property-labels).

### 4. Manage schema

Follow the general [setup instructions](./configure-connector.md#step-7-manage-schema).

### 5. Refresh settings

Follow the general [setup instructions](./configure-connector.md#step-8-refresh-settings).

[!NOTE]
>Identities are only refreshed in full crawls.
               
## Review & publish

Follow the general [setup instructions](./configure-connector.md#step-9-review-connection).

After publishing the connection, you need to customize the search results page. To learn about customizing search results, see [Customize the search results page](/microsoftsearch/configure-connector#next-steps-customize-the-search-results-page).

## Read and deny access to Knowledge articles in the ServiceNow Knowledge Microsoft Graph connector
Here is a scenario-wise depiction of how the connector treats access permissions based on user criteria in ServiceNow Knowledge.
               
>[!NOTE]
> Terms used in the table below:
> **No criteria** - No user criteria are defined for the article or Knowledge base. (Different from empty criteria where a user criteria is defined but within the criteria all fields are empty).
> **Default user criteria** - User criteria defined using ServiceNow fields like users, groups, roles, location, department etc.
> **Empty Criteria** - A usercriteria where all fields have empty values.

### How read access is determined

| Knowledge base |&nbsp;| Knowledge article | Access |
| :------ | :----- | :--- | :--- |
|**_Can read_** | **_Can contribute_**| **_Can read_**| |
| Any criteria | Any criteria | Default user criteria | Default user criteria followed |
| Any criteria | Any criteria | Default + Advanced criteria | Default user criteria followed. Advanced criteria ignored. |
| Any criteria | Any criteria | Empty criteria + Any criteria| Access provided to every ServiceNow user. |
| Default user criteria | Default user criteria | No criteria | Default user criteria followed. [_Note_: If the '_Cannot Contribute_' user criteria is not present, then default criteria from both '_Can read_' and '_Can Contribute_' are followed. **But if the '_Cannot Contribute_' user criteria is present, then '_Can Contribute_' user criteria is not stamped.**] |
| Default + Advanced criteria | Default + Advanced criteria | No criteria | Default user criteria followed. Advanced criteria ignored.|
| Empty criteria | Any criteria | No criteria | Access provided to every ServiceNow user. |

### How deny access is determined

| Knowledge base | Knowledge article | Access |
| :------ | :----- | :--- |
|**_Cannot read_** | **_Cannot read_**| |
| Default user criteria | Default user criteria | Both criteria at base and article level are honored. |
| Advanced criteria | Any criteria | Deny access to everyone. |
| Any criteria | Advanced criteria | Deny access to everyone. |
| Empty criteria + Default user criteria | Any criteria | Deny access to everyone. |
| Any criteria | Empty criteria | Deny access to everyone. |

## Limitations
>[!IMPORTANT]
>The ServiceNow Knowledge Microsoft Graph connector has the following limitations in its latest release:
>User criteria with advanced scripts aren't supported in the current version. For more information, see [Read and deny access to knowledge articles in the ServiceNow Knowledge Microsoft Graph connector](#read-and-deny-access-to-knowledge-articles-in-microsoft-graph-connector-for-servicenow).


## Troubleshooting
After publishing your connection, you can review the status under the **Data sources** tab in the [admin center](https://admin.microsoft.com). To learn how to make updates and deletions, see [Manage your connector](manage-connector.md).
You can find troubleshooting steps for commonly seen issues [here](troubleshoot-servicenow-knowledge-connector.md).

If you have any other issues or want to provide feedback, reach out to us at [Microsoft Graph | Support](https://developer.microsoft.com/en-us/graph/support)