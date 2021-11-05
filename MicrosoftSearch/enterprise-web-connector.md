---
title: "Enterprise websites Graph connector for Microsoft Search"
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
> ![Screenshot of Connection Settings pane for Enterprise Web connector.](media/enterprise-web-connector/connectors-enterpriseweb-connectionsettings-dynamicconfig-small.png)

In addition to the check box, there are three optional fields available:

1. **DOM Ready**: Enter the DOM element the crawler should use as the signal that the content is fully rendered and the crawl should begin.
1. **Headers to Add**: Specify which HTTP headers the crawler should include when sending that specific web URL. You can set multiple headers for different websites. We suggest including auth token values.
1. **Headers to Skip**: Specify any unnecessary headers that should be excluded from dynamic crawling requests.

> [!NOTE]
> Dynamic crawling is only supported for Agent crawl mode.

### Crawl mode: Cloud or On-premises

The crawl mode determines the type of websites you want to index, either cloud or on-premises. For your cloud websites, select **Cloud** as the crawl mode.

Also, the connector now supports crawling of on-premises websites. To access your on-premises data, you must first install and configure the Graph connector agent. To learn more, see [Graph connector agent](./graph-connector-agent.md).

For your on-premises websites, select **Agent** as the crawl mode and in the **On-prem Agent** field, choose the Graph connector agent that you installed and configured earlier.  

### Authentication

**Basic Authentication** requires a username and password.

**OAuth 2.0** with [Azure AD](/azure/active-directory/) requires a resource ID, Client ID, and Client Secret. OAuth 2.0 only works with Cloud mode.

The resource ID, client ID and client Secret values will depend on how you have done the setup for AAD based authentication for your website:
1. If you are using an application both as an identity provider and the client app to access the website, the Client ID and Resource ID will be the Application ID of the app and the Client Secret will be the Secret that you generated in the app. See [Quickstart: Register an application with the Microsoft identity platform and Configure your App Service or Azure Functions app to use Azure AD login](https://docs.microsoft.com/en-us/azure/app-service/configure-authentication-provider-aad) for steps to configure a client application as an Identity provider. After the client app is configured, make sure to create a new client secret by going to the Certificates & Secrets section of the app. Also, copy the client secret value shown in the page as it won't be shown again. See the screenshots below to know how to obtain Client ID and Client Secret and do setup required in the app if you are creating the app on your own.

Settings on branding page:
> ![branding](https://user-images.githubusercontent.com/92116746/140576543-eaf3df66-168d-49e2-bee6-696ea638744f.png)


Settings on authentication page:
> ![authentication](https://user-images.githubusercontent.com/92116746/140581216-00dcc775-6c96-4d66-9a03-bec21bcec57d.png)
Please note, it is not required for you to have the above specified route for Redirect URI in your website. If you will be using the user token sent by Azure in your website for authentication, only then you will need to have the route.


Client ID:
> ![clientAppClientIdResourceId](https://user-images.githubusercontent.com/92116746/140582329-964f87bf-36f7-442f-b2f4-d97220e1a709.png)


Client Secret:
> ![ClientSecret](https://user-images.githubusercontent.com/92116746/140582557-e6504b69-268e-4106-93cb-b23e72bc4a6a.png)


2. If you are using an application as an identity provider for your website, which will represent the resource, and a different application to access the website, the Client ID will be the application ID of your second app and the Client Secret will be the secret configured in the second app. However, the resource ID will be the ID of your first app. See [Quickstart: Register an application with the Microsoft identity platform](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app) and [Configure your App Service or Azure Functions app to use Azure AD login](https://docs.microsoft.com/en-us/azure/app-service/configure-authentication-provider-aad) for steps to configure a client application as an Identity provider. You don’t need to configure a client secret in this application. See the screenshots below to know how to complete the setup required in the app if you are creating the app on your own and how to obtain the client ID.

Settings on branding page:
> ![branding](https://user-images.githubusercontent.com/92116746/140576543-eaf3df66-168d-49e2-bee6-696ea638744f.png)

Settings on authentication page:
> ![authentication](https://user-images.githubusercontent.com/92116746/140581216-00dcc775-6c96-4d66-9a03-bec21bcec57d.png)
Please note, it is not required for you to have the above specified route for Redirect URI in your website. If you will be using the user token sent by Azure in your website for authentication, only then you will need to have the route.

Client ID:
> ![clientAppClientIdResourceId](https://user-images.githubusercontent.com/92116746/140582329-964f87bf-36f7-442f-b2f4-d97220e1a709.png)

You will also need to add an app role in the App roles section of the app which will later be assigned to your client application. See screenshots below on how to add an app role.
> ![newAppRole](https://user-images.githubusercontent.com/92116746/140583082-fe71762b-9501-4014-92c6-a73e16849077.png)

> ![newAppRole2](https://user-images.githubusercontent.com/92116746/140583088-d620e0f1-e642-442b-968e-de3060e7c22f.png)


After configuring the resource app, you need to create the client app and give it permissions to access the resource app by adding the app role configured above in the API permissions of the client app. See [Quickstart: Configure a client application to access a web API](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-configure-app-access-web-apis) and screenshots below to see how to grant permissions to the client app.
> ![AddingPermission](https://user-images.githubusercontent.com/92116746/140583143-1d897ce4-b6e1-4591-8115-62e07b39fb7d.png)

> ![AddingPermission2](https://user-images.githubusercontent.com/92116746/140583149-6c70c1f9-ffa8-4d2d-ac2f-171e77f37815.png)

> ![AddingPermission3](https://user-images.githubusercontent.com/92116746/140583154-6875d439-f523-40b1-829a-6328b5d5fc55.png)


Once the permissions are assigned, you will need to create a new client secret for this application by going to the Certificates & secrets section. Copy the client secret value shown in the page as it won't be shown again. Later use, the Application ID from this app as the Client ID, the secret from this app as the Client Secret and Application ID of the first app as the Resource ID in the admin center.


**Windows authentication** is only available in agent mode. It requires Username, Domain and Password. You need to provide the username and domain in the Username field in the format of either domain\username or username@domain. Password must be entered in the Password field. For Windows authentication, the username provided must also be an administrator in the server where the agent is installed.

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
