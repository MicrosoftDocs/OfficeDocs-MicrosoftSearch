---
ms.date: 09/06/2021
title: "Confluence Cloud Microsoft Graph connector"
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

# Confluence Cloud Microsoft Graph connector

Confluence Cloud Microsoft Graph connector allows your organization to index Confluence content. After you configure the connector and index data from the Confluence site, end users can search for those contents in Microsoft Search.

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors a Confluence Cloud connector. It supplements the general instructions provided in the [Set up Microsoft Graph connectors in the Microsoft 365 admin center](configure-connector.md) article. If you have not already done so, read the entire article to understand the general setup process.

Each step in the setup process is listed below along with either a note that indicates you should follow the general setup instructions OR other instructions that apply to only Confluence Cloud connector including information about [Troubleshooting](#troubleshooting) and [Limitations](#limitations).

## Before you get started

You must be the admin for your organization's Microsoft 365 tenant and the admin for your organization's Confluence site.

## Step 1: Add a connector in the Microsoft 365 admin center

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
2. Click on **Create** and select `OAuth 2.0 integration`.
3. Provide an appropriate name for the application and create the new app.
4. Navigate to `Permissions` from the navigation pane on left. Click **Add** for `Confluence API`. Once added, click on **Configure**, **Edit Scopes** and select the following scopes.

| **Scope Name** | **Code** | **Description** |
| ------------ | ------------ | ------------ |
| View content details | `read:content-details:confluence` | Crawl content satisfying criteria
| View groups | `read:group:confluence` | To access group permissions of content
| View user details | `read:user:confluence` | To access individual user details to support permissions

5. Click **Save**.
6. Navigate to `Authorization` from the navigation pane on the left. Add the callback URL, for **M365 Enterprise**: `https://gcs.office.com/v1.0/admin/oauth/callback`, for **M365 Government**: `https://gcsgcc.office.com/v1.0/admin/oauth/callback` and save the changes.
7. Navigate to `Settings` from the navigation pane on left. You will get the `Client ID` and `Secret` from this page.

On registering the app with the details above, you'll get the **Client ID** and **Secret**. Complete the connection settings step using these.

## Step 4: Select properties and filter data

In this step, you can add or remove available properties from your Confluence data source. Microsoft 365 has already selected few properties by default.

With a Confluence Query Language (CQL) string, you can specify conditions for syncing pages. It's like a **Where** clause in a **SQL Select** statement. For example, you can choose to index only the pages that are modified in the last two years. To learn about creating your own query string, see [Advanced Searching using CQL](https://developer.atlassian.com/server/confluence/advanced-searching-using-cql/). By default, all blogs and pages will be indexed by the connector.

>[!TIP]
>You may use the CQL filter to index **content modified after a certain time** using, *lastModified >= "2018/12/31"*

Use the preview results button to verify the sample values of the selected properties and CQL string.

## Step 5: Manage search permissions

Confluence Cloud Microsoft Graph connector supports search permissions visible to **Everyone** or **Only people with access to this data source**. If you choose **Everyone**, indexed data will appear in the search results for all users. If you choose **Only people with access to this data source**, indexed data will appear in the search results for users who have access to them.

In Confluence Cloud, security permissions for users and groups are defined using space permissions and page restrictions. Confluence Cloud connector applies space permissions if there are no page restrictions. Page level restrictions, if present, will take precedence over space permissions.

If you choose **Only people with access to this data source**, you need to further choose whether your Confluence site has Azure Active Directory (AAD) provisioned users or Non-AAD users.

To identify which option is suitable for your organization:

1. Choose the **AAD** option if the email ID of Confluence users is **same** as the UserPrincipalName (UPN) of users in AAD.
2. Choose the **Non-AAD** option if the email ID of Confluence users is **different** from the UserPrincipalName (UPN) of users in AAD.

>[!NOTE]
>
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

## Step 10: Set up search result page

After publishing the connection, you need to customize the search results page with verticals and result types. To learn about customizing search results, review how to [manage verticals](manage-verticals.md) and [result types](manage-result-types.md).
You may also use the [sample result layout](confluence-cloud-connector-result-layout.md) for the Confluence cloud connector. Simply copy-paste the result layout JSON to get started.

## Troubleshooting

Common errors observed while configuring the connector and their possible reasons are listed below.

| Configuration step | Error message | Possible reason(s) |
| ------------ | ------------ | ------------ |
| Connection settings | The request is malformed or incorrect. | Incorrect Confluence site URL |
| Connection settings | Unable to reach the Confluence cloud service for your Confluence site. | Incorrect Confluence site URL |
| Connection settings | The client doesn't have permission to perform the action. | Invalid API token provided for Basic auth |
| Select properties | No error message and no preview results | Check your CQL query whether it is valid |

## Limitations

The Confluence Cloud connector has the following known limitations in its latest release:

* Confluence Cloud connector does not index attachment files and comments.
* Indexing Server and Data Center deployments will be released as a separate connector.

