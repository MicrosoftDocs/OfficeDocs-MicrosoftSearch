--- 

title: "Zendesk Help Center Graph connector for Microsoft Search and Copilot" 
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
description: "Set up the Zendesk Help Center Microsoft Graph connector for Microsoft Search and Copilot" 
ms.date: 08/30/2024
---

# Zendesk Help Center Microsoft Graph connector (Preview)

The Zendesk Help Center Graph connector allows your organization to index articles from Zendesk Help Center (also known as Zendesk Guide). After you configure the connector, end users can search for these articles from Zendesk in Microsoft Copilot and from any Microsoft Search client.

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors a Zendesk Help Center Graph connector.

>[!NOTE]
>The Zendesk Help Center connector is in preview. If you wish to get early access to try it, sign up using [this form](https://forms.office.com/r/JniPmK5bzm).

## Capabilities
- Index Help Center articles
- Enable your end users to ask questions related to your support queries or product information in Copilot.
   - What is the return policy for apparels?
   - What are the product specifications for Surface laptop?
   - How can I upgrade my subscription?
- Use [Semantic search in Copilot](/MicrosoftSearch/semantic-index-for-copilot.md) to enable users to find relevant content based on keywords, personal preferences, and social connections.

## Limitations
- Doesn't support access restrictions to articles based on Zendesk user permissions. All users in your tenant have access to all indexed articles.
- Doesn't index Zendesk Guide Community posts and topics.
- Doesn't index attachments.

## Prerequisites
- You must be the **search admin** for your organization's Microsoft 365 tenant.
- **Zendesk Instance URL**: To connect to your Zendesk Help Center data, you need your organization's Zendesk Help Center instance URL. Your organization's Zendesk Help Center instance URL typically looks like `https://<your-organization-domain>.zendesk.com`. If you don't have an instance already, refer the [article](https://support.zendesk.com/hc/articles/4408823799962-How-do-I-create-a-Support-trial-account) to learn about creating a test instance.
- **Service Account**: To connect to Zendesk Help Center and allow Microsoft Graph Connector to update knowledge articles regularly, you need a service account with read permissions granted to the service account.

## Get Started

### 1. Display name 
A display name is used to identify each citation in Copilot, helping users easily recognize the associated file or item. Display name also signifies trusted content. Display name is also used as a [content source filter](/MicrosoftSearch/custom-filters#content-source-filters). A default value is present for this field, but you can customize it to a name that users in your organization recognize.

### 2. Zendesk URL
To connect to your Zendesk data, you need your organization's Zendesk instance URL. Your organization's Zendesk instance URL typically looks like `https://<your-organization-domain>.zendesk.com`.

### 3. Authentication Type
To authenticate and sync content from Zendesk, choose **one of the two** supported methods:<br>

   a. **Basic authentication** <br>
     Enter the username and password of Zendesk account to authenticate to your instance. 
     <br>

   b. **Zendesk OAuth (Recommended)**
   <details>
   <summary>[Click to expand] To use the Zendesk OAuth for authentication, follow these steps.</summary><br>

   A Zendesk admin needs to create an OAuth client in the [Zendesk Admin Center](https://support.zendesk.com/hc/articles/4581766374554-Using-Zendesk-Admin-Center). To learn more, see [Managing access to the Zendesk API](https://support.zendesk.com/hc/articles/4408889192858-Managing-access-to-the-Zendesk-API#topic_mmh_gm1_2yb) in the Zendesk documentation.

   The following table provides guidance on how to fill out the OAuth client creation form:

   Field | Description | Recommended Value
   --- | --- | ---
   Client name | Unique value that identifies the application that you require OAuth access for. | Microsoft Search
   Description | (Optional) A short description of the OAuth client | Use an appropriate description   
   Company | The name of your company | Use an appropriate value
   Logo | A file that contains the image for the application logo. | Any appropriate logo or use default.
   Client kind | Choose between Confidential and Public Oauth client | Confidential
   Redirect URL | A required callback URL that the authorization server redirects to. | For **M365 Enterprise**: https://<span>gcs.office.</span>com/v1.0/admin/oauth/callback,</br> For **M365 Government**: https://<span>gcsgcc.office.<span>com/v1.0/admin/oauth/callback
   
   Enter the client ID and Secret to connect to your instance. After connecting, use a Zendesk account credential to authenticate permission to crawl.
</details>

### 4. Rollout to limited audience
Deploy this connection to a limited user base if you want to validate it in Copilot and other Search surfaces before expanding the rollout to a broader audience. To know more about limited rollout, [click here](/MicrosoftSearch/staged-rollout-for-graph-connectors.md).

At this point, you're ready to create the connection for Zendesk Help Center. You can click on the "Create" button to publish your connection and index articles from your Zendesk account.

## Troubleshooting
After publishing your connection, you can review the status under the **Data Sources** tab in the [admin center](https://admin.microsoft.com). To learn how to make updates and deletions, see [Manage your connector](manage-connector.md).

If you have any other issues or want to provide feedback, reach out to us at [Microsoft Graph | Support](https://developer.microsoft.com/en-us/graph/support)
