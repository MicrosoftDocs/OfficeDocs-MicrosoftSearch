--- 

title: "Atlassian Jira Graph connector for Microsoft Search" 
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
description: "Set up the Atlassian Jira Graph connector for Microsoft Search" 
---

# Atlassian Jira Graph connector (preview)

The Atlassian Jira Graph connector allows your organization to index Jira issues. After you configure the connector and index content from the Jira site, end users can search for those items in Microsoft Search.

> [!NOTE]
> Read the [**Setup for your Graph connector**](configure-connector.md) article to understand the general Graph connectors setup instructions.

This article is for anyone who configures, runs, and monitors an Atlassian Jira Graph connector. It supplements the general setup process, and shows instructions that apply only for the Atlassian Jira Graph connector.

>[!IMPORTANT]
>The Atlassian Jira Graph connector supports only Jira cloud hosted instances. Jira Server and Jira Data Center versions are not supported by this connector.

## Before you get started
You must be the admin for your organization's M365 tenant as well as the admin for your organization's Jira site.

## Step 1: Add a Graph connector in the Microsoft 365 admin center
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
2. Click on `Create` and select `OAuth 2.0 integration`
3. Provide an appropriate name for the application and create the new app.
4. Navigate to `Permissions` from the navigation pane on left. Click `Add` for `Jira platform REST API`. Once added, click on `Configure` and add the following scopes - `View Jira issue data`, `Manage Jira global settings` and `View user profiles`.
5. Navigate to `Authorization` from the navigation pane on left. Add the callback URL `https://gcs.office.com/v1.0/admin/oauth/callback` and save the changes.
6. Navigate to `Settings` from the navigation pane on left. You will get the `Client ID` and `Secret` from this page.

On registering the app with the details above, you'll get the **Client ID** and **Secret**. Complete the connection settings step using these.

### Step 3a: Configure data: Select projects

You can choose for the connection to index either the entire Jira site or specific projects only.

* If you choose to index the entire Jira site, Jira issues in all projects in the site will get indexed. New projects and issues will be indexed during the next crawl after they're created.
* If you choose individual projects, only Jira issues in those projects will be indexed.

You may further choose to filter the Jira issues which will be indexed in 2 ways.
* Specify the **issue modified time period**. This will only index the Jira issues which are created or modified in the time period selected on a **rolling basis** based on current crawl.
* Specify the **JQL**. This will only index the Jira issues which are returned after filtering based on provided Jira Query Language (JQL). To learn more about using JQL, see Atlassian Support documentation on [using advanced search with Jira Query Language](https://support.atlassian.com/jira-service-management-cloud/docs/use-advanced-search-with-jira-query-language-jql/)

> [!TIP]
> You may use the JQL filter to index only specific Jira issue types using "*issueType in (Bug,Improvement)*"

### Step 3b: Configure data: Select properties

Select which fields you want the connection to index and preview data in these fields before proceeding. Some fields are already selected by default and cannot be removed.

The Atlassian Jira Graph connector can index both default issue fields as well as custom created issue fields.

> [!NOTE]
> If a selected custom created field is not present in some Jira issue type(s), the field will be ingested as *NULL* (blank).

## Step 4: Manage search permissions

The Atlassian Jira Graph connector supports search permissions visible to **Everyone** or **Only people with access to this data source**. If you choose **Everyone**, indexed data will appear in the search results for all users. If you choose **Only people with access to this data source**, indexed data will appear in the search results for users who have access to them. In Atlassian Jira, security permissions are defined using project permission schemes containing site-level groups and project roles. Issue level security can also be defined using issue-level permission schemes.

If you choose **Only people with access to this data source**, you need to further choose whether your Jira site has Azure Active Directory (AAD) provisioned users or Non-AAD users.

To identify which option is suitable for your organization:

1. Choose the **AAD** option if the Email ID of Jira users are **same** as the UserPrincipalName (UPN) of users in AAD.
2. Choose the **Non-AAD** option if the email ID of Jira users is **different** from the UserPrincipalName (UPN) of users in AAD. 

>[!NOTE]
> * If you choose AAD as the type of identity source, the connector maps the Email IDs of users obtained from Jira directly to UPN property from AAD.
> * If you chose "Non-AAD" for the identity type see [Map your non-Azure AD Identities](map-non-aad.md) for instructions on mapping the identities. You can use this option to provide the mapping regular expression from Email ID to UPN.

## Step 5: Assign property labels

Follow the general [setup instructions](./configure-connector.md).

## Step 6: Manage schema

Follow the general [setup instructions](./configure-connector.md).

## Step 7: Choose refresh settings

The Atlassian Jira Graph connector supports refresh schedules for both full and incremental crawls.
The recommended schedule is one hour for an incremental crawl and one day for a full crawl.

## Step 8: Review connection

Follow the general [setup instructions](./configure-connector.md).

## Troubleshooting
Underneath is a list of common errors observed while configuring the connector and their possible reasons.

| Configuration step | Error message | Possible reason(s) |
| ------------ | ------------ | ------------ |
| Connection settings | The request is malformed or incorrect. | Incorrect Jira site URL |
| Connection settings | Unable to reach the Jira cloud service for your Jira site. | Incorrect Jira site URL |
| Connection settings | The client doesn't have permission to perform the action. | Invalid API token provided for Basic auth |


## Limitations
The following are known limitations of the Atlassian Jira Graph connector:
* Jira Server and Data Center versions are not supported.