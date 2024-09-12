--- 

title: "WordPress.org Graph connector for Microsoft Search and Copilot" 
ms.author: rantang 
author: rantang
manager: jecui
audience: Admin
ms.audience: Admin 
ms.topic: article 
ms.service: mssearch 
ms.localizationpriority: Medium 
search.appverid: 
- BFB160 
- MET150 
- MOE150 
description: "Set up the WordPress.org-built website Microsoft Graph connector for Microsoft Search and Copilot" 
ms.date: 09/12/2024
---

# WordPress.org-built website Microsoft Graph connector (Preview)

With the Microsoft Graph connector for WordPress.org-built websites, your organization can index published posts and pages of your WordPress.org-built websites. After you configure the connector and index content from WordPress.org -built websites, end users can search for those published posts and pages in Microsoft Copilot and from any Microsoft Search client. 

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors a WordPress.org Graph connector. 

>[!NOTE]
>The "WordPress.org connector is in preview. If you wish to get early access to try it, sign up using [this form](https://forms.office.com/r/JniPmK5bzm).

## Capabilities
- Index published posts and pages of your WordPress.org-built website.    
- Choose what data you want to index.Currently choosing to index posts or pages and choosing to index posts associated to specific categories are supported.
- Customize your crawl frequency.  
- Create workflows using this connection and plugins from Microsoft Copilot Studio.  
- Use [Semantic search in Copilot](semantic-index-for-copilot.md) to enable users to find relevant content.

## Limitations
- Does not index comments. 
- Does not crawl user identities and access permissions. All published pages or posts indexed using the WordPress connector will be visible to all Microsoft 365 users in your tenant, from Microsoft Search or Copilot.

## Prerequisites
- You must be the **search admin** for your organization's Microsoft 365 tenant.
- **Install the Microsoft Graph connector agent**: To access your WordPress.org-built website, you must install and configure the [Microsoft Graph connector agent](https://learn.microsoft.com/en-US/microsoftsearch/graph-connector-agent). Please [download the agent installer](https://www.microsoft.com/en-us/download/details.aspx?id=104045) and follow the installation instructions to set it up. Once installed, ensure that the agent is configured correctly to connect your WordPress.org-built website with the graph connector. 
- **WordPress.org-built website URL**: To connect to your WordPress.org-built website data, you need your organization's WordPress.org-built website URL. 
- **WordPress.org-built website Admin account**: To connect to your WordPress.org-built website and allow Microsoft Graph Connector to update published posts and pages regularly, you need an admin user account of your WordPress.org-built website with the permission to create an application password.  Application password is used to authenticate with a third-party service or application that connects to your WordPress.org-built website via REST API. 

## Get Started

### 1. Display name 
A display name is used to identify each citation in Copilot, helping users easily recognize the associated file or item. Display name also signifies trusted content. Display name is also used as a [content source filter](/MicrosoftSearch/custom-filters#content-source-filters). A default value is present for this field, but you can customize it to a name that users in your organization recognize.

### 2. WordPress.org-built website URL
A WordPress.org-built website URL is the unique web address assigned to each WordPress.org-built website, allowing you to access your specific WordPress.org-built website.   

### 3. Graph Connector Agent
The graph connector agent acts as a bridge between your WordPress.org instance and the connector APIs, enabling secure and efficient data transfer. In this step, select the agent configuration you want to use for your connector.  

If you have not installed the [Microsoft Graph connector agent](https://learn.microsoft.com/en-US/microsoftsearch/graph-connector-agent) yet, you can  [download the agent installer](https://www.microsoft.com/en-us/download/details.aspx?id=104045) and follow the installation instructions to set it up. Once installed, ensure that the agent is configured correctly to connect your on-premises WordPress.org instance with the graph connector. 

### 4. Authentication Type
We support the basic authentication method. To enable and configure basic authentication in WordPress.org, please find more details [here](https://make.wordpress.org/core/2020/11/05/application-passwords-integration-guide/).  

### 5. Staged rollout to limited audience
Deploy this connection to a limited user base if you want to validate it in Copilot and other Search surfaces before expanding the rollout to a broader audience.

At this point, you are ready to create the connection for WordPress.org-built website. You can click on the ‘**Create**’ button to publish your connection and index published posts and pages from your WordPress.org-built website.  

For other settings, like Access Permissions, Data inclusion rules, Schema, Crawl frequency etc., we have set defaults based on what works best with WordPress.org-built website data. You can see the default values below: 









## Troubleshooting
After publishing your connection, you can review the status under the **Data Sources** tab in the [admin center](https://admin.microsoft.com). To learn how to make updates and deletions, see [Manage your connector](manage-connector.md).

If you have any other issues or want to provide feedback, reach out to us at [Microsoft Graph | Support](https://developer.microsoft.com/en-us/graph/support)
