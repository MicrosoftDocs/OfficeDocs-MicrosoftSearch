--- 
title: "Azure DevOps Wiki Microsoft Graph connector for Microsoft Search and Microsoft 365 Copilot" 
ms.author: vivg 
author: vivg 
manager: harshkum 
audience: Admin
ms.audience: Admin 
ms.topic: article 
ms.service: mssearch 
ms.localizationpriority: Medium 
search.appverid: 
- BFB160 
- MET150 
- MOE150 
description: "Set up the Azure DevOps Wiki Microsoft Graph connector for Microsoft Search and Microsoft 365 Copilot" 
ms.date: 06/03/2022
---

# Azure DevOps Wiki Microsoft Graph connector

The Azure DevOps Wiki Microsoft Graph connector allows your organization to index wikis in its instance of the Azure DevOps service. After you configure the connector, end users can search for project wikis and code wikis from Azure DevOps in Microsoft Search and Microsoft 365 Copilot.

This article is for anyone who configures, runs, and monitors an Azure DevOps Wiki Microsoft Graph connector. It supplements the general setup process and shows instructions that apply only to the Azure DevOps Wiki Microsoft Graph connector.

> [!NOTE]
> Read the [**Setup for your Graph connector**](configure-connector.md) article to understand the general Graph connectors setup instructions.

>[!IMPORTANT]
>The Azure DevOps Wiki Microsoft Graph connector supports only the Azure DevOps cloud service. Azure DevOps Server 2019, TFS 2018, TFS 2017, TFS 2015, and TFS 2013 are not supported by this connector.

## Before you get started

You must be the **search admin** for your organization's Microsoft 365 tenant as well as the admin for your organization's Azure DevOps instance.

To allow the connector to connect to your Azure DevOps organization, you must enable **Third-party application access via OAuth**. Refer Azure DevOps documentation to [manage security policies](/azure/devops/organizations/accounts/change-application-access-policies?view=azure-devops#manage-a-policy&preserve-view=true) to learn more.

![Third-party application access via OAuth](media/ado-workitems-connector-security-policies.png)

You need the following permissions granted to the user account whose credentials are used during the connector configuration:

| Permission name | Permission type | Required for |
| ------------ | ------------ | ------------ |
| View project-level information | [Project permission](/azure/devops/organizations/security/permissions?view=azure-devops&tabs=preview-page#project-level-permissions&preserve-view=true) | Crawling Azure DevOps Work Items. This permission is **mandatory** for the projects that need to be indexed. |

>[!IMPORTANT]
>The user account must have **Basic** access level. To learn more about access levels in Azure DevOps, read [supported access levels](/azure/devops/organizations/security/access-levels).

## Step 1: Add a Microsoft Graph connector in the Microsoft 365 admin center

[Add Azure DevOps Wiki Microsoft Graph connector](https://admin.microsoft.com/adminportal/home#/MicrosoftSearch/Connectors/add?ms_search_referrer=MicrosoftSearchDocs_AzureDevOpsWiki&type=AzureDevOpsWiki)

Follow the general [setup instructions](./configure-connector.md).

## Step 2: Name the connection

Follow the general [setup instructions](./configure-connector.md).

## Step 3: Configure the connection settings

To authenticate and sync content from Azure DevOps, choose **one of the two** supported methods:<br>

> [!IMPORTANT]
> - [Microsoft Entra ID OAuth](/azure/devops/integrate/get-started/authentication/oauth?preserve-view=true&view=azure-devops) is in preview and available to select customers. This is the recommended OAuth mechanism.
> - [Azure DevOps OAuth](/azure/devops/integrate/get-started/authentication/oauth?preserve-view=true&view=azure-devops) is the legacy authentication mechanism, not being actively invested upon.

### Microsoft Entra ID OAuth (Preview)

**Ensure your ADO Organization is connected to Microsoft Entra**

The Azure DevOps Graph connector only indexes content from an ADO organization connected with Microsoft Entra of your tenant. To ensure that your ADO organization is connected with Microsoft Entra account, use the following steps. 

1. Navigate to [Azure DevOps](https://dev.azure.com/) and select the required organization.
2. Select `Organization settings`.
3. On the left navigation pane, select `Microsoft Entra` under the 'General' header.
4. Ensure that the organization is connected to your tenant's Microsoft Entra account.

**Create an app on Microsoft Entra ID**

1. Go to the [Azure portal](https://portal.azure.com) and sign in with admin credentials for the tenant.
2. Navigate to **Microsoft Entra ID** -> **Manage** -> **App registrations** from the navigation pane and select **New registration**.
3. Provide a name for the app and select **Register**.
4. Make a note of the Application (client) ID. This ID is used to grant the Microsoft Entra app access to projects in the ADO organization.
5. Open **API permissions** from the navigation pane and select **Add a permission**.
6. Select **Azure DevOps** and then **Delegated permissions**.
7. Search for the following permissions and select **Add permissions**. <br>
    a. Identity (read) <br>
    b. Code (read) <br>
    c. Entitlements (read) <br>
    d. Project and Team (read) <br>
    e. Graph (read) <br>
    f. MemberEntitlement Management (read) <br>
    g. Wiki (read)
8. Select **Grant admin consent for [TenantName]** and confirm by selecting **Yes**.
9. Check that the permissions are in the "**Granted**" state.
10. Open **Authentication** from the navigation pane. Select `Add a platform` and choose `Web`. Add one of the following URIs under "Redirect URIs":
    - For **M365 Enterprise**: `https://gcs.office.com/v1.0/admin/oauth/callback`
    - For **M365 Government**: `https://gcsgcc.office.com/v1.0/admin/oauth/callback`
11. Under **Implicit grant and hybrid flows**, check the option for `ID tokens (used for implicit and hybrid flows)` and click **Configure**.
12. From the navigation pane, select **Certificates and secrets** under **Manage**.
13. Select **New Client secret** and select an expiry period for the secret. Copy the generated secret (Value) and save it because it isn't shown again.
14. Use this Client secret and the application ID to configure the connector.

**Grant the Microsoft Entra app access to projects in the ADO organization**

You need to provide the Microsoft Entra app the necessary access to the projects which need to be indexed using the following steps:

1. Navigate to [Azure DevOps](https://dev.azure.com/) and select the required organization.
2. Select `Organization settings`.
3. On the left navigation pane, select `Users` under the 'General' header.
4. Select `Add users`.
5. Copy the Application (client) ID obtained from the app to "Users or Service Principals".
6. Grant the `Basic` access level and select the projects to allow access to index. Also add to the `Project Reader` Azure DevOps group (or equivalent) to ensure access. De-select the option to send email invitation to users.

### Azure DevOps OAuth

To connect to your Azure DevOps instance, you need your Azure DevOps organization App ID and client secret for OAuth authentication.

**Register an app**

Register an app in Azure DevOps so that the Microsoft Search app and Microsoft 365 Copilot can access the instance. To register the app, visit the link to [register application]( https://app.vsaex.visualstudio.com/app/register). To learn more, see Azure DevOps documentation on how to [register an app](/azure/devops/integrate/get-started/authentication/oauth?preserve-view=true&view=azure-devops#register-your-app).

The following table provides guidance on how to fill out the app registration form:

Mandatory fields | Description | Recommended value
--- | --- | ---
| Company name         | The name of your company. | Use an appropriate value.|
| Application name     | A unique value that identifies the application that you're authorizing.    | Microsoft Search.|
| Application website  | The URL of the application that requests access to your Azure DevOps instance during connector setup. (required).| For **Microsoft 365 Enterprise**: https://<span>gcs.office.</span>com/,</br> For **Microsoft 365 Government**: https://<span>gcsgcc.<span>office.com/|
| Authorization callback URL| A required callback URL that the authorization server redirects to. | For **Microsoft 365 Enterprise**: https://<span>gcs.office.</span>com/v1.0/admin/oauth/callback,</br> For **Microsoft 365 Government**: https://<span>gcsgcc.office.<span>com/v1.0/admin/oauth/callback|
| Authorized scopes | The scope of access for the application | Select the following scopes: Identity (read), Code (read), Entitlements (read), Project and Team (read), Graph (read), Member Entitlement Management (read), Wiki (read).|


>[!IMPORTANT]
>The authorized scopes selected for the app should exactly match the scopes listed above. If either more or less scopes are selected, authorization fails.

When On registering the app, you get the **App ID** and **Client Secret** that is used to configure the connector.

To revoke access to any app registered in Azure DevOps, go to User settings at the right top of your Azure DevOps instance. Select **Profile** and then select **Authorizations** in the Security section of the side pane. Hover over an authorized OAuth app to see the Revoke button at the corner of the app details.

### Connection settings

After registering the Microsoft Search app and Microsoft 365 Copilot with Azure DevOps, you can complete the connection settings step. Enter your App ID and client secret.

![Connection Application Settings.](media/azure-devops-wiki-connection-settings.png)

### Configure data: select organization, projects, and fields
  
In this step, you specify the scope of data that you want to index using the Azure DevOps Wiki Microsoft Graph connector.

As the first step, you choose the organization you want to index, out of all organizations you have access to. You can then choose for the connection to index either the entire organization or specific projects within the selected organization.

If you choose to index the entire organization, wikis in all projects in the organization are indexed. New projects and wikis are indexed during the next crawl after they're created.

If you choose to index individual projects, only wikis in the selected projects are indexed.

## Step 4: Manage search permissions

The Azure DevOps Wiki Microsoft Graph connector supports search permissions visible to **Everyone**. With the **Everyone** option, indexed data appears in the search results for all users.

## Step 5: Assign property labels

Follow the general [setup instructions](./configure-connector.md).

## Step 6: Manage schema

Follow the general [setup instructions](./configure-connector.md).

## Step 7: Choose refresh settings

The Azure DevOps Wiki Microsoft Graph connector supports refresh schedules for both full and incremental crawls.
The recommended schedule is one hour for an incremental crawl and one week for a full crawl.

## Step 8: Review connection

Follow the general [setup instructions](./configure-connector.md).

## Step 9: Set up search result page

After publishing the connection, you need to customize the search results page with verticals and result types. To learn about customizing search results, review how to [manage verticals](manage-verticals.md) and [result types](manage-result-types.md).

  You may also use the [sample result layout](azure-devops-wiki-connector-result-layout.md) for the Azure DevOps Wiki Microsoft Graph connector. Simply copy-paste the result layout JSON to get started.

## Troubleshooting
  
After publishing your connection, you can review the status under the **Data sources** tab in the [admin center](https://admin.microsoft.com). To learn how to make updates and deletions, see [Manage your connector](manage-connector.md).
You can find troubleshooting steps for commonly seen issues [here](troubleshoot-azure-devops-wiki-connector.md).

If you have issues or want to provide feedback, contact [Microsoft Graph | Support (https://developer.microsoft.com/en-us/graph/support).
