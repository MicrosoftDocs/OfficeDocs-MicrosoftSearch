--- 

title: "Azure DevOps Wiki Graph connector for Microsoft Search" 
ms.author: vivg 
author: vivg 
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
description: "Set up the Azure DevOps Wiki Microsoft Graph connector for Microsoft Search" 
---

# Azure DevOps Wiki Microsoft Graph connector (preview)

The Azure DevOps Wiki Graph connector allows your organization to index wikis in its instance of the Azure DevOps service. After you configure the connector, end users can search for project wikis and code wikis from Azure DevOps in Microsoft Search.

> [!NOTE]
> * The Azure DevOps Wiki Graph connector is in preview. If you wish to get early access to try it, sign up using [this form](https://forms.office.com/r/JniPmK5bzm).
> * Read the [**Setup for your Graph connector**](configure-connector.md) article to understand the general Graph connectors setup instructions.

This article is for anyone who configures, runs, and monitors an Azure DevOps Wiki Graph connector. It supplements the general setup process, and shows instructions that apply only for the Azure DevOps Wiki Graph connector.

>[!IMPORTANT]
>The Azure DevOps Wiki connector supports only the Azure DevOps cloud service. Azure DevOps Server 2019, TFS 2018, TFS 2017, TFS 2015, and TFS 2013 are not supported by this connector.

<!---## Before you get started-->
## Before you get started
You must be the **search admin** for your organization's M365 tenant as well as the admin for your organization's Azure DevOps instance.

To allow the connector to connect to your Azure DevOps Organization, you must enable **Third-party application access via OAuth**. Refer Azure DevOps documentation to [manage security policies](/azure/devops/organizations/accounts/change-application-access-policies?view=azure-devops#manage-a-policy&preserve-view=true) to learn more.

![Third-party application access via OAuth](media/ado-workitems-connector-security-policies.png)

The Azure DevOps Wiki Connector crawls documents using an [OAuth Client App](/azure/devops/integrate/get-started/authentication/oauth?view=azure-devops) with the [on-behalf-of OAuth flow](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow). You will need the following permissions granted to the user account whose credentials are used during the connector configuration for each Azure DevOps organization to be crawled:

| Permission name | OAuth Scope | Description | Required for |
| ------------ | ------------ | ------------ | ------------ |
| Project and team (read) | vso.project | Grants the ability to read projects and teams. | Enumerating the list of projects to be crawled. |
| Wiki (read) | vso.wiki | Grants the ability to read wikis, wiki pages and wiki attachments. Also grants the ability to search wiki pages. | Enumerating the list of wikis and wiki pages to be crawled. | 
| Code (read) | vso.code | Grants the ability to read source code and metadata about commits, changesets, branches, and other version control artifacts. Also grants the ability to search code and get notified about version control events via service hooks. | Reading a list of changes to wiki pages, which are stored in git repositories, for incremental crawls. |
| Entitlements (read) | vso.entitlements | Provides read only access to licensing entitlements endpoint to get account entitlements. | Enumerating user licenses for creating access control lists |
| Member Entitlement Management (read) | vso.memberentitlementmanagement | Grants the ability to read users, their licenses as well as projects and extensions they can access. | Enumerating user licenses for creating access control lists |
| Graph (read) | vso.graph | Grants the ability to read user, group, scope, and group membership information. | Enumerating user group memeberships for creating access control lists. |
| Identity (read) | vso.identity | Grants the ability to read identities and groups. | Enumerating a list of users and groups for creating access control lists |

## Step 1: Add a Graph connector in the Microsoft 365 admin center

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup 
instructions.-->

## Step 2: Name the connection

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup 
instructions.-->

## Step 3: Configure the connection settings

To connect to your Azure DevOps instance, you need your Azure DevOps account App ID and client secret for OAuth authentication.

### Register an app

Register an app in Azure DevOps so that the Microsoft Search app can access the instance. To learn more, see Azure DevOps documentation on how to [register an app](/azure/devops/integrate/get-started/authentication/oauth?preserve-view=true&view=azure-devops#register-your-app).

The following table provides guidance on how to fill out the app registration form:

Mandatory Fields | Description | Recommended Value
--- | --- | ---
| Company Name         | The name of your company. | Use an appropriate value   |
| Application name     | A unique value that identifies the application that you're authorizing.    | Microsoft Search     |
| Application website  | The URL of the application that will request access to your Azure DevOps instance during connector setup. (Required).  | https://<span>gcs.office.</span>com/
| Authorization callback URL        | A required callback URL that the authorization server redirects to. | https://<span>gcs.office.</span>com/v1.0/admin/oauth/callback|
| Authorized scopes | The scope of access for the application | Select the following scopes: Identity (read), Code (read), Entitlements (read), Project and team (read), Graph (read), MemberEntitlement Management (read), Wiki (read) |

>[!IMPORTANT]
>The authorized scopes selected for the app should exactly match the scopes listed above. If either more or less scopes are selected, authorization will fail.

On registering the app with the details above, you'll get the **App ID** and **Client Secret** that will be used to configure the connector.

>[!NOTE]
>To revoke access to any app registered in Azure DevOps, go to User settings at the right top of your Azure DevOps instance. Select Profile and then select Authorizations in the Security section of the side pane. Hover over an authorized OAuth app to see the Revoke button at the corner of the app details.

### Connection settings

After registering the Microsoft Search app with Azure DevOps, you can complete the connection settings step. Enter your App ID and Client secret.

![Connection Application Settings.](media/azure-devops-wiki-connection-settings.png)

### Configure data: select organization, projects and fields
In this step, you specify the scope of data which you want to index using the Azure DevOps Wiki graph connector.

As the first step, you can choose the organization you want to index, out of all organizations you have access to. You can then choose for the connection to index either the entire organization or specific projects within the selected organization.

If you choose to index the entire organization, wikis in all projects in the organization will get indexed. New projects and wikis will be indexed during the next crawl after they're created.

If you choose to index individual projects, only wikis in the selected projects will be indexed.

## Step 4: Manage search permissions

The Azure DevOps connector supports search permissions visible to **Only people with access to this data source** or **Everyone**. If you choose **Only people with access to this data source**, indexed data will appear in the search results for users who have access to them based on permissions to users or groups at the Organization, Project, or Wiki level in Azure DevOps. If you choose **Everyone**, indexed data will appear in the search results for all users.

## Step 5: Assign property labels

Follow the general [setup instructions](./configure-connector.md).

## Step 6: Manage schema

Follow the general [setup instructions](./configure-connector.md).

## Step 7: Choose refresh settings

The Azure DevOps Wiki connector supports refresh schedules for both full and incremental crawls.
The recommended schedule is one hour for an incremental crawl and one week for a full crawl.

## Step 8: Review connection

Follow the general [setup instructions](./configure-connector.md).

<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup 
instructions.-->

## Step 9: Set up search result page

After publishing the connection, you need to customize the search results page with verticals and result types. To learn about customizing search results, review how to [manage verticals](manage-verticals.md) and [result types](manage-result-types.md).
You may also use the [sample result layout](azure-devops-wiki-connector-result-layout.md) for the Azure DevOps Wiki connector. Simply copy-paste the result layout JSON to get started.

<!---## Troubleshooting-->
<!---Insert troubleshooting recommendations for this data source-->

<!---## Limitations-->
<!---Insert limitations for this data source-->
