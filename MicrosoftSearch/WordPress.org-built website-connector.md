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

