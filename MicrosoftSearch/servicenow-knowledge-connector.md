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
description: "Set up the ServiceNow Knowledge Graph connector for Microsoft Search and Copilot."
---
<!---Previous ms.author: kam1 --->

# ServiceNow Knowledge Microsoft Graph connector

With the Microsoft Graph connector for ServiceNow, your organization can index knowledge-base articles that are visible to all users or restricted with user criteria permissions within your organization. After you configure the connector and index content from ServiceNow, end users can search for those articles in Microsoft Copilot and from any Microsoft Search client.

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors a ServiceNow Knowledge Graph connector.

## Capabilities
- Index all types of knowledge articles
- Enable your end users to ask questions related to your IT/HR workflows in Copilot.
   - How to request a new device?
   - How to create a new VPN connection?
   - How do I apply for leaves?
- Use [Semantic search in Copilot](/MicrosoftSearch/semantic-index-for-copilot.md) to enable users to find relevant content based on keywords, personal preferences, and social connections.

## Limitations
- Doesn't support [Advanced scripts](https://docs.servicenow.com/bundle/xanadu-servicenow-platform/page/product/knowledge-management/task/create-user-criteria-record-in-knowledge-management.html).
- If both Knowledge base and Knowledge article level permissions are defined, then only article-level permissions are honored.
- Does not index attachments.

## Prerequisites
- **ServiceNow Instance URL**: To connect to your ServiceNow data, you need your organization's ServiceNow instance URL. Your organization's ServiceNow instance URL typically looks like https://your-organization-name.service-now.com. (Don’t have one? [Check how to create a test instance](https://www.youtube.com/watch?v=OTdzVLqpFHY))
- **Service Account**: To connect to ServiceNow and allow Microsoft Graph Connector to update knowledge articles regularly, you need a service account with read access to specific ServiceNow table records. The service account needs read access to the following **ServiceNow table records** to successfully crawl various entities.

   Feature | Read access required tables | Description
   --- | --- | ---
   Index knowledge articles available to <em>Everyone</em> | kb_knowledge | For crawling knowledge articles
   Index and support user criteria permissions | kb_uc_can_read_mtom | Who can read this knowledge base
   | | kb_uc_can_contribute_mtom | Who can contribute to this knowledge base
   | | kb_uc_cannot_read_mtom | Who cannot read this knowledge base
   | | kb_uc_cannot_contribute_mtom | Who cannot contribute to this knowledge base
   | | sys_user | Read user table
   | | sys_user_has_role | Read role information of users
   | | sys_user_grmember | Read group membership of users
   | | user_criteria | Read user criteria permissions
   | | kb_knowledge_base | Read knowledge base information
   | | sys_user_group | Read user group segments
   | | sys_user_role | Read user roles
   | | cmn_location | Read location information
   | | cmn_department | Read department information
   | | core_company | Read company attributes
   Index extended table properties (optional) | sys_db_object | Read extended table details
   | | sys_dictionary | Read extended table properties

   You can **create and assign a role** for the service account you use to connect with Microsoft Search. [Learn how to assign role for ServiceNow accounts](https://docs.servicenow.com/bundle/vancouver-platform-administration/page/administer/users-and-groups/task/t_AssignARoleToAUser.html). Read access to the tables can be assigned on the created role. To learn about setting read access to table records, see [Securing Table Records](https://developer.servicenow.com/dev.do#!/learn/learning-plans/vancouver/new_to_servicenow/app_store_learnv2_securingapps_vancouver_creating_and_editing_access_controls). 

   If you want to index properties from [extended tables](https://docs.servicenow.com/bundle/vancouver-platform-administration/page/administer/table-administration/concept/table-extension-and-classes.html) of *kb_knowledge*, provide read access to sys_dictionary and sys_db_object. The access to these tables is optional. You can index *kb_knowledge* table properties without access to the two additional tables.

## Get Started

![Connection creation screen for Microsoft Graph Connector for ServiceNow Knowledge](/MicrosoftSearch/media/servicenow-knowledge-create-page.png "Add Microsoft Graph Connector for ServiceNow Knowledge")

###1. Display name 
A display name is used to identify each reference in Copilot, helping users easily recognize the associated file or item. Display name also signifies trusted content. Display name is also used as a [content source filter](/MicrosoftSearch/custom-filters#content-source-filters). A default value is present for this field, but you can customize it to a name that users in your organization recognize.

###2. ServiceNow URL
To connect to your ServiceNow data, you need your organization's ServiceNow instance URL. Your organization's ServiceNow instance URL typically looks like https://your-organization-name.service-now.com.

###3. Authentication Type
To authenticate and sync content from ServiceNow, choose **one of three** supported methods:<br>

   a. **Basic authentication** <br>
     Enter the username and password of ServiceNow account with **knowledge** role to authenticate to your instance.
     <br>

   b. **ServiceNow OAuth (Recommended)**
   <details>
   <summary>[Click to expand]To use the ServiceNow OAuth for authentication, follow these steps.</summary><br>
    
   A ServiceNow admin needs to provision an endpoint in your ServiceNow instance, so that the Graph connector can access it. To learn more, see [Create an endpoint for clients to access the instance](https://docs.servicenow.com/bundle/vancouver-platform-security/page/administer/security/task/t_CreateEndpointforExternalClients.html) in the ServiceNow documentation.

   The following table provides guidance on how to fill out the endpoint creation form:

   Field | Description | Recommended Value
   --- | --- | ---
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

   3. Retrieve Service Principal Object Identifier

      Follow the steps to retrieve Service Principal Object Identifier

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
   
            Replace "Application-ID" with Application (client) ID (without quotes) of the application you registered in step 1. Note the value of ID object from PowerShell output. It's the Service Principal ID.

            Now you have all the information required from Azure portal. A quick summary of the information is given in the table below.

         Property | Description
         --- | ---
         Directory ID (Tenant ID) | Unique ID of the Microsoft Entra tenant, from step 3.a.
         Application ID (Client ID) | Unique ID of the application registered in step 3.a.
         Client Secret | The secret key of the application (from step 3.b). Treat it like a password.
         Service Principal ID | An identity for the application running as a service. (from step 3.c)

   4. Register ServiceNow Application

      The ServiceNow instance needs the following configuration:

         1. Register a new OAuth OIDC entity. To learn, see [Create an OAuth OIDC provider](https://docs.servicenow.com/bundle/vancouver-platform-security/page/administer/security/task/add-OIDC-entity.html).

         1. The following table provides guidance on how to fill out OIDC provider registration form

              Field | Description | Recommended Value
              --- | --- | ---
              Name | A unique name that identifies the OAuth OIDC entity. | Microsoft Entra ID
              Client ID | The client ID of the application registered in the third-party OAuth OIDC server. The instance uses the client ID when requesting an access token. | Application (Client) ID from step 3.a
              Client Secret | The client secret of the application registered in the third-party OAuth OIDC server. | Client Secret from step 3.b

            All other values can be default.

         1. In the OIDC provider registration form, you need to add a new OIDC provider configuration. Select the search icon against *OAuth OIDC Provider Configuration* field to open the records of OIDC configurations. Select New.

         1. The following table provides guidance on how to fill out OIDC provider configuration form

             Field | Recommended Value
             --- | ---
             OIDC Provider |  Microsoft Entra ID
             OIDC Metadata URL | The URL must be in the form https\://login.microsoftonline.com/<tenandId">/.well-known/openid-configuration <br/>Replace "tenantID" with Directory (tenant) ID from step 3.a.
             OIDC Configuration Cache Life Span |  120
             Application | Global
             User Claim | sub
             User Field | User ID
             Enable JTI claim verification | Disabled

         1. Select Submit and Update the OAuth OIDC Entity form.

   5. Create a ServiceNow account

      Refer the instructions to create a ServiceNow account, [create a user in ServiceNow](https://docs.servicenow.com/bundle/vancouver-platform-administration/page/administer/users-and-groups/task/t_CreateAUser.html).

      The following table provides guidance on how to fill out the ServiceNow user account registration

      Field | Recommended Value
       --- | ---
      User ID | Service Principal ID from step 3.c 
      Web service access only | Checked

      All other values can be left to default.

   6. Enable Knowledge role for the ServiceNow account

      Access the ServiceNow account you created with ServiceNow Principal ID as User ID and assign the knowledge role. Instructions to assigning a role to a ServiceNow account can be found here, [assign a role to a user](https://docs.servicenow.com/bundle/vancouver-platform-administration/page/administer/users-and-groups/task/t_AssignARoleToAUser.html). Refer to the table mentioned under Service account in the [Prerequisites](#prerequisites) section for providing read access to more ServiceNow table records and index user criteria permissions.

      Use Application ID as Client ID (from step 3.1), and Client secret (from step 3.2) in admin center configuration wizard to authenticate to your ServiceNow instance using Microsoft Entra ID OpenID Connect.

</details>

###4. Rollout to limited audience
Deploy this connection to a limited user base if you want to validate it in Copilot and other Search surfaces before expanding the rollout to a broader audience. To know more about limited rollout, click [here](/MicrosoftSearch/staged-rollout-for-graph-connectors.md).

At this point, you are ready to create the connection for ServiceNow Knowledge. You can click on the "Create" button and the Microsoft Graph connector will start indexing articles from your ServiceNow account.

For other settings, like Access Permissions, Data inclusion rules, Schema, Crawl frequency etc., we have set defaults based on what works best with ServiceNow data. You can see the default values below:

|**Users** ||
|----|---|
|Access permissions|_Only people with access to content in Data source._|
|Map Identities|_Data source identities mapped using Microsoft Entra IDs._|

|**Content**||
|---|---|
|Query String|_active=true^workflow_state=published_|
|Manage Properties|_To check default properties and their schema, click here_|

|**Sync**||
|---|---|
|Incremental Crawl|_Frequency: Every 15 mins_|
|Full Crawl|_Frequency: Every Day_|

If you want to edit any of these values, you need to choose the "Custom Setup" option.

[Get started with Microsoft Graph Connector for ServiceNow Knowledge](https://admin.microsoft.com/adminportal/home#/MicrosoftSearch/Connectors/add?ms_search_referrer=MicrosoftSearchDocs_ServiceNowKB&type=ServiceNowKB)


##Custom Setup

Custom setup is for those admins who want to edit the default values for settings listed in the above table. Once you click on the "Custom Setup" option, you see three more tabs – Users, Content, and Sync.

###Users

![Users tab where you can configure access permissions and user mapping rules](/MicrosoftSearch/media/servicenow-knowledge-users-tab.png "Configure settings related to Users")

**Access Permissions**

The ServiceNow connector supports access permissions visible to "Everyone" or "Only people with access to content in data source". Indexed data appears in results and is visible to all users in the organization or users who have access to them via user criteria permission respectively. Choose the one that is most appropriate for your organization.

If a knowledge article isn't enabled with a user criterion, it appears in results of everyone in the organization.

>[!IMPORTANT]
>In ServiceNow, while assessing read permissions for a user, both article-level permissions and KB-level permissions are looked at. The Microsoft Graph connector for ServiceNow treats permissions differently:
>1. If the article contains '_Can Read_' user criteria, then they are stamped on the article during ingestion and Knowledge Base '_Can Read_' / '_Can Contribute_' user criteria are ignored.
>2. If the article contains '_Cannot Read_' user criteria, and if the corresponding Knowledge base also contains '_Cannot Read_' user criteria, then both the user criteria are stamped on the article.

>**Note**: If a user is part of the '_Can Read_' user criteria at the article level but not in the '_Can Read_' / '_Can Contribute_' user criteria at the Knowledge Base level, **then the user will not have access to the article in ServiceNow but will have access to the article in Microsoft Copilot, Microsoft Search and other M365 surfaces**. The workaround is to remove the user from the '_Can Read_' user criteria at the article level.

**Mapping Identities**

The default method for mapping your data source identities with Microsoft Entra ID is by checking whether the Email id of ServiceNow users is same as the UserPrincipalName (UPN), or Mail of the users in Microsoft Entra ID. If you believe the default mapping would not work for your organization, you can provide a custom mapping formula. To know more about, mapping Non-EntraID identities, click [here](/MicrosoftSearch/map-non-aad.md).

###Content

![Content tab where you can configure Query string and Properties](/MicrosoftSearch/media/servicenow-knowledge-content-tab.png "Configure settings related to your content")

**Query String**

*The list of properties that you select here, can impact how can you filter, search and view your results in Copilot for Microsoft 365.*

**Source property** | **Label** | **Description**
--- | --- | ---
AccessUrl  | `url` | The target URL of the item in the data source.
Author   | `authors` | Name of all the people who participated/collaborated on the item in the data source.
IconUrl   | `iconUrl` | Icon url that represents the article’s category or type.
Short_description  | `title` | The title of the item that you want shown in search and other experiences.
SysUpdatedBy   | `lastModifiedBy` | Name of the person who most recently edited the item in the data source.
SysUpdatedOn  | `lastModifiedDateTime` | Date and time the item was last modified in the data source.
SysCreatedBy   | `createdBy` | Name of the person who created the item in the data source.
SysCreatedOn   | `createdDateTime` | Date and time that the item was created in the data source.

With a ServiceNow query string, you can specify conditions for syncing articles. It's like a **Where** clause in a **SQL Select** statement. For example, you can choose to index only articles that are published and active. To learn about creating your own query string, see [Generate an encoded query string using a filter](https://docs.servicenow.com/bundle/vancouver-platform-user-interface/page/use/using-lists/task/t_GenEncodQueryStringFilter.html).

**Manage Properties**

Here, you can add or remove available properties from your ServiceNow data source, assign a schema to the property (define whether a property is searchable, queryable, retrievable or refinable), change the semantic label and add an alias to the property. Properties that are selected by default are listed below.

|Source Property|Label|Description|Schema|
|---|---|---|---|
|AccessURL|url|The target URL of the item in the data source|Retrieve|
|Active||||
|ArticleType||||
|Author|authors|Name all the people who participated/collaborated on the item in the data source|Search, Query, Retrieve|
|CanReadUserCriteria||||
|CannotReadUserCriteria||||
|Content||||
|EntityType||||
|IconURL|iconUrl|Icon url that represents the article's category or type.|Retrieve|
|KbKnowledgeBase||||
|Number|||Retrieve|
|PreviewContent|||Retrieve|
|Short_description|title|The title of the item that you want shown in Copilot and other search experiences|Search, Retrieve|
|SysCreatedBy|createdBy|Name of the person who created the item in the data source.|Retrieve|
|SysCreatedOn|CreatedDateTime|Data and time that the item was created in the data source|Retrieve|
|SysUpdatedBy|lastModifiedBy|Name of the person who most recently edited the item in the data source.|Retrieve|
|SysUpdatedOn|lastModifiedDateTime|Date and time the item was last modified in the data source.|Retrieve|
|WorkflowState|||Retrieve|

**Preview Data**

Use the preview results button to verify the sample values of the selected properties and query filter.

![Preview data option to check the query filter and properties you have configured](/MicrosoftSearch/media/servicenow-knowledge-preview-data.png "Preview data to validate your Query filter and Manage Properties settings")

###Sync

![Sync tab where you can configure crawl frequency](/MicrosoftSearch/media/servicenow-knowledge-sync-tab.png "Configure Crawl frequency")

The refresh interval determines how often your data is synced between the data source and the Graph connector index. There are two types of refresh intervals – full crawl and incremental crawl. For more details, click [here](/MicrosoftSearch/configure-connector#step-8-refresh-settings).

You can change the default values of refresh interval from here if you want to.

## Read and Deny Access to Knowledge Articles in Microsoft Graph Connector for ServiceNow
<details>
<summary>[Click to expand] Here is a scenario-wise depiction of how the connector treats access permissions based on user criteria in ServiceNow Knowledge:</summary><br>

>[!NOTE]
> Terms used in the table below:
> * **No criteria**: No user criteria is defined for the article or Knowledge base. (Different from empty criteria where a user criteria is defined but within the criteria all fields are empty)
> * **Default user criteria**: User criteria defined using ServiceNow fields like Users, Groups, Roles, Location, Department etc.
>* **Empty Criteria**: A User criteriion where all fields have empty values.

### How Read access is determined

| Knowledge Base |&nbsp;| Knowledge Article | Access |
| :------ | :----- | :--- | :--- |
|**_Can read_** | **_Can contribute_**| **_Can read_**| |
| Any criteria | Any criteria | Default user criteria | Default user criteria followed |
| Any criteria | Any criteria | Default + Advanced criteria | Default user criteria followed. Advanced criteria ignored. |
| Any criteria | Any criteria | Empty criteria + Any criteria| Access provided to every ServiceNow user |
| Default user criteria | Default user criteria | No criteria | Default user criteria followed. [_Note_: If the '_Cannot Contribute_' user criteria is not present, then default criteria from both '_Can read_' and '_Can Contribute_' are followed. **But if the '_Cannot Contribute_' user criteria is present, then '_Can Contribute_' user criteria is not stamped.**] |
| Default + Advanced criteria | Default + Advanced criteria | No criteria | Default user criteria followed. Advanced criteria ignored.|
| Empty criteria | Any criteria | No criteria | Access provided to every ServiceNow user |

### How Deny access is determined

| Knowledge Base | Knowledge Article | Access |
| :------ | :----- | :--- |
|**_Cannot read_** | **_Cannot read_**| |
| Default user criteria | Default user criteria | Both criteria at base and article level are honored. |
| Advanced criteria | Any criteria | Deny access to everyone. |
| Any criteria | Advanced criteria | Deny access to everyone. |
| Empty criteria + Default user criteria | Any criteria | Deny access to everyone. |
| Any criteria | Empty criteria | Deny access to everyone. |
</details>

## Troubleshooting
After publishing your connection, you can review the status under the **Data Sources** tab in the [admin center](https://admin.microsoft.com). To learn how to make updates and deletions, see [Manage your connector](manage-connector.md).
You can find troubleshooting steps for commonly seen issues [here](troubleshoot-servicenow-knowledge-connector.md).

If you have any other issues or want to provide feedback, reach out to us at [Microsoft Graph | Support](https://developer.microsoft.com/en-us/graph/support)
