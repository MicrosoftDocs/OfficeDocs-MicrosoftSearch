---
title: "Enterprise websites Graph connector for Microsoft Search"
ms.author: mecampos
author: mecampos
manager: umas
audience: Admin
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Set up the Enterprise websites Graph connector for Microsoft Search"
---
<!---Previous ms.author: monaray --->

<!-- markdownlint-disable no-inline-html -->

# Enterprise websites Graph connector

The Enterprise websites Graph connector allows your organization to index articles and **content from its internal-facing websites**. After you configure the connector and sync content from the website, end users can search for that content from any Microsoft Search client.

> [!NOTE]
> Read the [**Setup your Graph connector**](configure-connector.md) article to understand the general Graph connectors setup instructions.

This article is for anyone who configures, runs, and monitors an Enterprise websites connector. It supplements the general setup process, and shows instructions that apply only for the Enterprise websites connector. This article also includes information about [Troubleshooting](#troubleshooting).

<!---## Before you get started-->

<!---Insert "Before you get started" recommendations for this data source-->

## Step 1: Add a Graph connector in the Microsoft 365 admin center

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 2: Name the connection

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Step 3: Configure the connection settings

To connect to your data source, fill in the root URL of the website, select a crawl source, and the type of authentication you'd like to use: None, Basic Authentication, or OAuth 2.0 with [Azure Active Directory (Azure AD)](/azure/active-directory/). After you complete this information, select Test Connection to verify your settings.

### URL

Use the URL field to specify the root of the website that you'd like to crawl. The enterprise websites connector will use this URL as the starting point and follow all the links from this URL for its crawl.

### Crawl websites listed in the sitemap

When selected the connector will only crawl the URLs listed in the sitemap. If not selected or no site map is found, the connector will do a deep crawl of all the links found on the root URL of the site.

### Dynamic site configuration

If your website contains dynamic content, for example, webpages that live in content management systems like Confluence or Unily, you can enable a dynamic crawler. To turn it on, select **Enable crawl for dynamic sites**. The crawler will wait for dynamic content to render before it begins crawling.

> [!div class="mx-imgBorder"]
> [![Screenshot of Connection Settings pane for Enterprise Web connector](media/enterprise-web-connector/connectors-enterpriseweb-connectionsettings-dynamicconfig-small.png)](media/enterprise-web-connector/connectors-enterpriseweb-connectionsettings-dynamicconfig.png#lightbox)

In addition to the check box, there are three optional fields available:

1. **DOM Ready**: Enter the DOM element the crawler should use as the signal that the content is fully rendered and the crawl should begin.
1. **Headers to Add**: Specify which HTTP headers the crawler should include when sending that specific web URL. You can set multiple headers for different websites. We suggest including auth token values.
1. **Headers to Skip**: Specify any unnecessary headers that should be excluded from dynamic crawling requests.

> [!NOTE]
> Dynamic crawling is only supported for Agent crawl mode.

### Crawl mode: Cloud or On-premises

The crawl mode determines the type of websites you want to index, either cloud or on-premises. For your cloud websites, select **Cloud** as the crawl mode.

Also, the connector now supports crawling of on-premises websites. To access your on-premises data, you must first install and configure the Graph connector agent. To learn more, see [Graph connector agent](./on-prem-agent.md).

For your on-premises websites, select **Agent** as the crawl mode and in the **On-prem Agent** field, choose the Graph connector agent that you installed and configured earlier.  

### Authentication

Basic Authentication requires a username and password. Create this bot account by using the [Microsoft 365 admin center](https://admin.microsoft.com).

OAuth 2.0 with [Azure AD](/azure/active-directory/) requires a resource ID, Client ID, and Client Secret. OAuth 2.0 only works with Cloud mode.

For more information, see [Authorize access to Azure Active Directory web applications using OAuth 2.0 code grant flow](/azure/active-directory/develop/v1-protocols-oauth-code). Register with the following values:

**Name:** Microsoft Search <br/>
**Redirect_URI:** `https://gcs.office.com/v1.0/admin/oauth/callback`

To get the values for the resource, client_id, and client_secret, go to **Use the authorization code to request an access token** on the redirect URL webpage.

For even more information, see [Quickstart: Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app).

## Step 3a: Add URLs to exclude (Optional crawl restrictions)

There are two ways to prevent pages from being crawled: disallow them in your robots.txt file or add them to the Exclusion list.

### Support for robots.txt

The connector checks to see if there is a robots.txt file for your root site and, if one exists, it will follow and respect the directions found within that file. If you do not want the connector to crawl certain pages or directories on your site, you can call out those pages or directories in the "Disallow" declarations in your robots.txt file.

### Add URLs to exclude

You can optionally create an **Exclusion list** to exclude some URLs from getting crawled if that content is sensitive or not worth crawling. To create an exclusion list, browse through the root URL. You can add the excluded URLs to the list during the configuration process.

## Step 4: Assign property labels

You can assign a source property to each label by choosing from a menu of options. While this step isn't mandatory, having some property labels will improve the search relevance and ensure more accurate search results for end users.

## Step 5: Manage schema

On the **Manage Schema** screen, you can change the schema attributes (the options are **Query**, **Search**, **Retrieve**, and **Refine**) associated with the properties, add optional aliases, and choose the **Content** property.

## Step 6: Manage search permissions

The Enterprise websites connector only supports search permissions visible to **Everyone**. Indexed data appears in the search results and is visible to all users in the organization.

## Step 7: Set the refresh schedule

The Enterprise websites connector only supports a full refresh. This means that the connector will recrawl all the website's content during every refresh. To make sure the connector gets enough time to crawl the content, we recommend that you set a large refresh schedule interval. We recommend a scheduled refresh between one and two weeks.

## Step 8: Review connection

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup instructions.-->

## Troubleshooting

When reading the website's content, the crawl may encounter some source errors, which are represented by the detailed error codes below. To get more information on the types of errors, go to the **error details** page after selecting the connection. Select the **error code** to see more detailed errors. Also refer to [Manage your connector](./manage-connector.md) to learn more.

 Detailed Error code | Error message
 --- | ---
 6001 | The site that is being tried to index is not reachable
 6005 | The source page that is being tried to index has been blocked by as per robots.txt configuration.
 6008 | Unable to resolve the DNS
 6009 | For all client-side errors (Except HTTP 404, 408), refer to HTTP 4xx error codes for details.
 6013 | The source page that is being tried to index could not be found. (HTTP 404 error)
 6018 | The source page is not responding, and the request has timed out. (HTTP 408 error)
 6021 | The source page that is being tried to index has no textual content on the page.
 6023 | The source page that is being tried to index is unsupported (not an HTML page)
 6024 | The source page that is being tried to index has unsupported content.

* Errors 6001-6013 occur when the data source is not reachable due to a network issue or when the data source itself is deleted, moved, or renamed. Check if the data source details provided are still valid.
* Errors 6021-6024 occur when the data source contains non-textual content on the page or when the page is not an HTML. Check the data source and add this page in exclusion list or ignore the error.
