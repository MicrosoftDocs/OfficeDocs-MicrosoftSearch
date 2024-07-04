--- 

title: "Atlassian Jira Cloud Microsoft Graph connector" 
ms.author: mecampos 
author: mecampos 
manager: umas 
audience: Admin
ms.audience: Admin 
ms.topic: article 
ms.service: mssearch 
ms.localizationpriority: medium 
search.appverid: 
- BFB160 
- MET150 
- MOE150 
description: "Set up the Atlassian Jira Cloud Graph connector for Microsoft Search" 
ms.date: 07/22/2021
---

# Atlassian Jira Cloud Microsoft Graph connector

The Atlassian Jira Cloud Microsoft Graph connector allows your organization to index Jira issues. After you configure the connector and index content from the Jira site, end users can search for those items in Microsoft Search.

> [!NOTE]
> Read the [**Set up Microsoft Graph connectors in the Microsoft 365 admin center**](configure-connector.md) article to understand the general connectors setup instructions.

This article is for anyone who configures, runs, and monitors an Atlassian Jira Cloud connector. It supplements the general setup process, and shows instructions that apply only for the Atlassian Jira Cloud connector.

>[!IMPORTANT]
>The Atlassian Jira Cloud connector supports only Jira cloud hosted instances. Jira Server and Jira Data Center versions are not supported by this connector.

## Before you get started

You must be the admin for your organization's Microsoft 365 tenant and the admin for your organization's Jira site.

You'll need the following permissions granted to the user account whose credentials are used during the connector configuration:

| Permission name | Permission type | Required for |
| ------------ | ------------ | ------------ |
| Browse projects | [Project permission](https://support.atlassian.com/jira-cloud-administration/docs/manage-project-permissions/) | Crawling Jira issues. This permission is **mandatory** for the projects that need to be indexed. |
| Issue level security permissions | [Issue-level security](https://support.atlassian.com/jira-cloud-administration/docs/configure-issue-security-schemes/) | Crawling different issue types. This permission is **optional**. |
| Browse users and groups   | [Global permission](https://support.atlassian.com/jira-cloud-administration/docs/manage-global-permissions/) | ACL trimming of search results. This permission is **optional** and is required to select `Only people with access to this data source` option in step 4 below. |
| Administer Jira | [Global permission](https://support.atlassian.com/jira-cloud-administration/docs/manage-global-permissions/) | ACL trimming of search results. This permission is **optional** and is required to select `Only people with access to this data source` option in step 4 below. |

## Step 1: Add a connector in the Microsoft 365 admin center

[Add Jira connector](https://admin.microsoft.com/adminportal/home#/MicrosoftSearch/Connectors/add?ms_search_referrer=MicrosoftSearchDocs_Jira&type=Jira)

Follow the general [setup instructions](./configure-connector.md).

## Step 2: Name the connection
Follow the general [setup instructions](./configure-connector.md).

## Step 3: Configure the connection settings
To connect to your Jira site, use your Jira site URL. A Jira cloud site URL typically looks like *https://<organization_name>.atlassian.net/*. You can choose either Basic Authentication or OAuth 2.0 (recommended) to authenticate to your Jira site.

### Basic Auth
Enter your account's username (usually email ID) and API token to authenticate using basic auth. To learn more about generating an API token, refer Atlassian's documentation on how to [manage API tokens for your Atlassian account](https://support.atlassian.com/atlassian-account/docs/manage-api-tokens-for-your-atlassian-account/).

### OAuth 2.0
Register an app in Atlassian Jira so that the Microsoft Search app can access the instance. To learn more, see Atlassian Support documentation on how to [Enable OAuth 2.0](https://developer.atlassian.com/cloud/jira/platform/oauth-2-3lo-apps/#enabling-oauth-2-0--3lo-).

The following steps provide guidance on how to register the app:

1. Sign in to [Atlassian Developer console](https://developer.atlassian.com/console/myapps/) with your Atlassian Jira admin account.
2. Select on `Create` and select `OAuth 2.0 integration`.
3. Provide an appropriate name for the application and create the new app.
4. Navigate to `Permissions` from the navigation pane on left. Under the 'Granular Permissions' header, select `Add` for `Jira API`. Once added, select on `Configure` and add the following scopes listed below.

   | **#** | **Scope name** | **Code** |
   | ------------ | ------------ | ------------ |
   | 1 | View fields | `read:field:jira` |
   | 2 | View avatars | `read:avatar:jira` |
   | 3 | View project categories | `read:project-category:jira` |
   | 4 | View projects | `read:project:jira` |
   | 5 | Read field configurations | `read:field-configuration:jira` |
   | 6 | View issue types | `read:issue-type:jira` |
   | 7 | View project properties | `read:project.property:jira` |
   | 8 | View users | `read:user:jira` |
   | 9 | View application roles | `read:application-role:jira` |
   | 10 | View groups | `read:group:jira` |
   | 11 | Read issue type hierarchies | `read:issue-type-hierarchy:jira` |
   | 12 | View project versions | `read:project-version:jira` |
   | 13 | View project components | `read:project.component:jira` |
   | 14 | View issue details | `read:issue-details:jira` |
   | 15 | View audit logs | `read:audit-log:jira` |
   | 16 | View issue meta | `read:issue-meta:jira` |
   | 17 | View project roles | `read:project-role:jira` |
   | 18 | View issue security levels | `read:issue-security-level:jira` |
   | 19 | View issue security schemes | `read:issue-security-scheme:jira` |
   | 20 | View permission schemes | `read:permission-scheme:jira` |
   | 21 | View permissions | `read:permission:jira` |

5. Navigate to `Authorization` from the navigation pane on the left. Add the callback URL for **M365 Enterprise**: `https://gcs.office.com/v1.0/admin/oauth/callback`, for **M365 Government**: `https://gcsgcc.office.com/v1.0/admin/oauth/callback` and save the changes.
6. Navigate to `Settings` from the navigation pane on the left. You'll get the `Client ID` and `Secret` from this page.

Complete the connection settings step using the **Client ID** and **Secret**.

> [!NOTE]
>
> * Refer the [list of scopes](https://developer.atlassian.com/cloud/jira/platform/scopes-for-oauth-2-3LO-and-forge-apps/#list-of-scopes) for OAuth 2.0 apps to learn more about Jira permissions.
> * The original (Classic) OAuth permissions are being deprecated for Jira cloud. Refer the [changelog announcement](https://developer.atlassian.com/cloud/jira/platform/changelog/#CHANGE-517) to learn more.

### Step 3a: Configure data: Select projects

You can choose for the connection to index either the entire Jira site or specific projects only.

* If you choose to index the entire Jira site, Jira issues in all projects in the site will get indexed. New projects and issues will be indexed during the next crawl after they're created.
* If you choose individual projects, only Jira issues in those projects will be indexed.

> [!NOTE]
> When you grant the _Browse projects_ permission to a Jira projects, it will be listed, and it can be crawled. If a project is missing, check the permissions for your account.

You may further choose to filter the Jira issues that will be indexed in two ways.

* Specify the **issue modified time period**. This will only index the Jira issues that are created or modified in the time period selected on a **rolling basis** based on current crawl.
* Specify the **JQL**. This will only index the Jira issues that are returned after filtering based on provided Jira Query Language (JQL). To learn more about using JQL, see Atlassian Support documentation on [using advanced search with Jira Query Language](https://support.atlassian.com/jira-service-management-cloud/docs/use-advanced-search-with-jira-query-language-jql/)

> [!TIP]
> You may use the JQL filter to index only specific Jira issue types using "*issueType in (Bug,Improvement)*"

### Step 3b: Configure data: Select properties

Select which fields you want the connection to index and preview data in these fields before proceeding. Some fields are already selected by default and can't be removed.

The Atlassian Jira connector can index both default issue fields and custom created issue fields.

*The list of properties that you select here, can impact how you can filter, search and view your results in Copilot for Microsoft 365.* 

**Source property** | **Label** | **Description**
--- | --- | ---
Authors   | `authors` | Name of people who participated/collaborated on the item in the data source.
Created  | `createdDateTime` | Date and time that the item was created in the data source.
IssueIconUrl  | `iconUrl` | The associated icon url with specific issue priority.
IssueLink  | `url` | The target URL of the item in the data source.
ReporterEmailId   | `createdBy` | Name of the person who most recently edited the item in the data source.
Title   | `title` | The title of the item that you want shown in search and other experiences.
Updated  | `lastModifiedDateTime` | Date and time the item was last modified in the data source.

> [!NOTE]
> If a selected custom created field is not present in some Jira issue type(s), the field will be ingested as *NULL* (blank).

## Step 4: Manage search permissions

The Atlassian Jira connector supports search permissions visible to **Everyone** or **Only people with access to this data source**. If you choose **Everyone**, indexed data will appear in the search results for all users. If you choose **Only people with access to this data source**, indexed data will appear in the search results for users who have access to them. In Atlassian Jira, security permissions are defined using project permission schemes containing site-level groups and project roles. Issue level security can also be defined using issue-level permission schemes.

>[!IMPORTANT]
>The Jira cloud Graph connector must be able to read a user’s email id in Jira to appropriately assign security permissions in Microsoft Search. This requires you to ensure either of the following:
- All users should have selected the ‘Anyone’ option for their profile visibility settings. To learn more about profile visibility settings, refer the [documentation by Atlassian](https://support.atlassian.com/atlassian-account/docs/update-your-profile-and-visibility-settings/).
- For organizations using ‘Managed accounts’ (All the Atlassian accounts with email addresses from your verified domain become managed accounts. Refer [this documentation](https://support.atlassian.com/user-management/docs/what-are-managed-accounts/) for more information) - 
>    * All users, who are part of managed accounts, must have the managed account setting selected in profile visibility settings.
>    * Users who are not part of the managed account (same as crawling account), need to have ‘Anyone’ selected in their profile visibility settings.
>    * The crawling account used during connection configuration must have the managed account domain.

If you choose **Only people with access to this data source**, you need to further choose whether your Jira site has Microsoft Entra ID provisioned users or Non-Azure AD users.

To identify which option is suitable for your organization:

1. Choose the **Microsoft Entra ID** option if the Email ID of Jira users is the **same** as the UserPrincipalName (UPN) of users in Microsoft Entra ID.
2. Choose the **Non-Azure AD** option if the email ID of Jira users is **different** from the UserPrincipalName (UPN) of users in Microsoft Entra ID.

>[!NOTE]
> * If you choose Microsoft Entra ID as the type of identity source, the connector maps the Email IDs of users obtained from Jira directly to UPN property from Microsoft Entra ID.
> * If you chose "Non-Azure AD" for the identity type see [Map your non-Azure AD Identities](map-non-Azure AD.md) for instructions on mapping the identities. You can use this option to provide the mapping regular expression from Email ID to UPN.
> * Updates to users or groups governing access permissions are synced in full crawls only. Incremental crawls do not currently support processing of updates to permissions.

## Step 5: Assign property labels

Follow the general [setup instructions](./configure-connector.md).

## Step 6: Manage schema

Follow the general [setup instructions](./configure-connector.md).

## Step 7: Choose refresh settings

The Atlassian Jira connector supports refresh schedules for both full and incremental crawls.
The recommended schedule is one hour for an incremental crawl and one day for a full crawl.

## Step 8: Review connection

Follow the general [setup instructions](./configure-connector.md).

After publishing the connection, you need to customize the search results page. To learn about customizing search results, see [Customize the search results page](/microsoftsearch/configure-connector#next-steps-customize-the-search-results-page).

## Step 9: Set up search result page

After publishing the connection, you need to customize the search results page with verticals and result types. To learn about customizing search results, review how to [manage verticals](manage-verticals.md) and [result types](manage-result-types.md).
You may also use the [sample result layout](jira-connector-result-layout.md) for Jira connector. Simply copy-paste the result layout JSON to get started.

## Troubleshooting

Below is a list of common errors observed while configuring the connector or during crawls, and their possible reasons.

| Step | Error message | Possible reason(s) |
| ------------ | ------------ | ------------ |
| Connection settings | The request is malformed or incorrect. | Incorrect Jira site URL. |
| Connection settings | Unable to reach the Jira cloud service for your Jira site. | Incorrect Jira site URL. |
| Connection settings | The client doesn't have permission to perform the action. | Invalid API token provided for Basic auth. |
| Connection settings | "Something went wrong" error in OAuth pop-up window. | The scopes granted to OAuth app don't match. The mismatched scopes are listed in the pop-up window. |
| Crawl time (post connector configuration) | Can't authenticate with data source. Verify the credentials associated with this data source are correct. | The user doesn't have one or more permissions required to crawl Jira. |
| Crawl time (post connector configuration) | You don't have permission to access this data source. You can contact the owner of this data source to request permission. | If you're using OAuth, the app scopes may have changed, or the app may have expired or deleted. <br> If you're using basic authentication, the API token may have expired or deleted. |
| Crawl time (post connector configuration) | Error code: 1003 - You don't have permission to access this data source. <br> Detailed error code: 7612 | The crawl account does not have "Browse projects" permission for the listed project (under 'item id' column). |

## Limitations

The following are known limitations of the Atlassian Jira connector:

* The connector does not support the "Any user logged in" application role to grant access to issues.
* Jira Server and Data Center versions aren't supported.
