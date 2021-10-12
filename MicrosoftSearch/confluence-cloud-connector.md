---
title: "Confluence Cloud Graph connector for Microsoft Search"
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
description: "Set up the Confluence Cloud Graph connector for Microsoft Search"
---
<!---Previous ms.author: kam1 --->

# Confluence Cloud Graph Connector (Preview)

Confluence Cloud Graph connector allows your organization to index Confluence content. After you configure the connector and index data from the Confluence site, end users can search for those content in Microsoft Search.

>[!NOTE]
>Confluence Cloud Graph Connector is in preview. If you wish to get early access to try it, sign up using [<b> this form </b>](https://forms.office.com/r/duLxv8Nf8U).  

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors a Confluence Cloud Graph connector. It supplements the general instructions provided in the [Set up your Graph connector](configure-connector.md) article. If you have not already done so, read the entire Set up your Graph Connector article to understand the general setup process.

Each step in the setup process is listed below along with either a note that indicates you should follow the general setup instructions OR other instructions that apply to only Confluence Cloud Graph connector including information about [Troubleshooting](#troubleshooting) and [Limitations](#limitations).


## Before you get started
You must be the admin for your organization's M365 tenant as well as the admin for your organization's Confluence site.

## Step 1: Add a Graph connector in the Microsoft 365 admin center
Follow the general [setup instructions](./configure-connector.md).

## Step 2: Name the connection
Follow the general [setup instructions](./configure-connector.md).

## Step 3: Configure the connection settings
To connect to your Confluence site, use your site URL. A Confluence cloud site URL typically looks like *https://<organization_name>.atlassian.net/*. You can choose either Basic Authentication or OAuth 2.0 (recommended) to authenticate to your Confluence site. 

>[!TIP]
>Make sure the service **account has view access** to the Confluence content you want to index.
### Basic Auth
Enter your account's username (usually email ID) and API token to authenticate using basic auth. To learn more about generating an API token, refer Atlassian's documentation on how to [manage API tokens for your Atlassian account](https://support.atlassian.com/atlassian-account/docs/manage-api-tokens-for-your-atlassian-account/).

### OAuth 2.0 (recommended)
Register an app in Confluence Cloud so that the Microsoft Search app can access the instance. To learn more, see Atlassian Support documentation on how to [Enable OAuth 2.0](https://developer.atlassian.com/cloud/confluence/oauth-2-3lo-apps/#enabling-oauth-2-0--3lo-).

The following steps provide guidance on how to register the app:

1. Sign in to [Atlassian Developer console](https://developer.atlassian.com/console/myapps/) with your Atlassian Confluence admin account.
2. Click on `Create` and select `OAuth 2.0 integration`
3. Provide an appropriate name for the application and create the new app.
4. Navigate to `Permissions` from the navigation pane on left. Click `Add` for `Confluence API`. Once added, click on `Configure` and add the following scopes - `Read Confluence space summary`, `Read Confluence content properties`, `Read Confluence detailed content`, `Read Confluence content summary`, `Read content permission in Confluence`, `Read user`, `Read user groups` and `Search Confluence content and space summaries`.
5. Navigate to `Authorization` from the navigation pane on left. Add the callback URL `https://gcs.office.com/v1.0/admin/oauth/callback` and save the changes.
6. Navigate to `Settings` from the navigation pane on left. You will get the `Client ID` and `Secret` from this page.

On registering the app with the details above, you'll get the **Client ID** and **Secret**. Complete the connection settings step using these.

## Step 4: Select properties and filter data

In this step, you can add or remove available properties from your Confluence data source. Microsoft 365 has already selected few properties by default.

With a Confluence Query Language (CQL) string, you can specify conditions for syncing pages. It's like a **Where** clause in a **SQL Select** statement. For example, you can choose to index only the pages that are modified in the last two years. To learn about creating your own query string, see [Advanced Searching using CQL](https://developer.atlassian.com/server/confluence/advanced-searching-using-cql/). By default, all blogs and pages will be indexed by the connector.

Use the preview results button to verify the sample values of the selected properties and CQL string.

## Step 5: Manage search permissions

Confluence Cloud Graph connector supports search permissions visible to **Everyone** or **Only people with access to this data source**. If you choose **Everyone**, indexed data will appear in the search results for all users. If you choose **Only people with access to this data source**, indexed data will appear in the search results for users who have access to them.

In Confluence Cloud, security permissions for users and groups are defined using space permissions and page restrictions. Confluence Cloud Graph Connector applies space permissions if there are no page restrictions. Page level restrictions, if present, will take precedence over space permissions.

If you choose **Only people with access to this data source**, you need to further choose whether your Confluence site has Azure Active Directory (AAD) provisioned users or Non-AAD users.

To identify which option is suitable for your organization:

1. Choose the **AAD** option if the Email ID of Confluence users are **same** as the UserPrincipalName (UPN) of users in AAD.
2. Choose the **Non-AAD** option if the email ID of Confluence users is **different** from the UserPrincipalName (UPN) of users in AAD. 

>[!NOTE]
> * If you choose AAD as the type of identity source, the connector maps the Email IDs of users obtained from Confluence directly to UPN property from AAD.
> * If you chose "Non-AAD" for the identity type see [Map your non-Azure AD Identities](map-non-aad.md) for instructions on mapping the identities. You can use this option to provide the mapping regular expression from Email ID to UPN.

## Step 6: Assign property labels

Follow the general [setup instructions](./configure-connector.md).

## Step 7: Manage schema

Follow the general [setup instructions](./configure-connector.md).

## Step 8: Choose refresh settings

Follow the general [setup instructions](./configure-connector.md).

>[!NOTE]
>For access permission updates, only full crawl scheduled will be applied.

## Step 9: Review Connection

Follow the general [setup instructions](./configure-connector.md).

After publishing the connection, you need to customize the search results page. To learn about customizing search results, see [Customize the search results page](/microsoftsearch/configure-connector#next-steps-customize-the-search-results-page).

## Troubleshooting
Underneath is a list of common errors observed while configuring the connector and their possible reasons.

| Configuration step | Error message | Possible reason(s) |
| ------------ | ------------ | ------------ |
| Connection settings | The request is malformed or incorrect. | Incorrect Confluence site URL |
| Connection settings | Unable to reach the Confluence cloud service for your Confluence site. | Incorrect Confluence site URL |
| Connection settings | The client doesn't have permission to perform the action. | Invalid API token provided for Basic auth |
| Select properties | No error message and no preview results | Check your CQL query whether it is valid |

## Limitations
Confluence Cloud Graph connector has the following known limitations in its latest release:

- Confluence Cloud Connector does not index attachment files and comments.
- Indexing Server and Data Center deployments will be released as a separate connector.