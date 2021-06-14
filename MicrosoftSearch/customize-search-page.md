---
title: "Manage verticals"
ms.author: jeffkizn
author: jypal
manager: jeffkizn
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Add search verticals and customize search results"
---
# Managing verticals

**<Add some text here>**

## Things to consider

Before you start, make sure that the connector has been indexed. This can take up to 48 hours, depending on the file size.

You can’t create a vertical for content that resides in [SharePoint](https://sharepoint.com/).

There are three basic steps to add a vertical:

1. Create the vertical. In this step, you define the vertical’s name, content source, and scope of the content to search.
1. Define what the results for this vertical will look like.
1. Define a query variables for the vertical.
1. Enable the vertical.

## Create the search vertical

After you start the wizard, you're guided through the steps to define the vertical's name, content source, and scope of the content to search. The vertical is created in a disabled state. You'll enable it later.

You can use a limited set of [Keyword Query Language (KQL)](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference) to narrow the scope. This page lists the properties that are available. We recommend that you use free-text keywords and property restrictions with boolean operators for creating the KQL.

### Create a vertical at the organization level

To create the vertical on Microsoft Search in [SharePoint](https://sharepoint.com/) home, [Office](https://office.com), or [Bing](https://bing.com), follow these steps:

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to [**Verticals**](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/verticals).
2. Select **Add** to get started.  

### Create a vertical at the site level

1. On the [SharePoint](https://sharepoint.com/) site where you want the vertical, go to **Settings**.
2. Select **Site information** and then **View all site settings**.
3. Look for the **Microsoft Search** section, and then select **Configure Microsoft Search for this site collection**.
4. In the navigation pane, go to **Custom experience**, and then select the **Verticals** tab.
5. To add a vertical, select **Add**.
  Or, to edit a vertical, select it in the list.

Verticals are created in a disabled state. They must be enabled before users can see them.

## View the vertical after it's enabled

After you enable the vertical, it will take a few hours before you can view it. If you don't want to wait after enabling it, you can append **cacheClear=true** to the URL in [SharePoint](https://sharepoint.com/) and [Office](https://office.com) to view the vertical immediately. For [Bing](https://bing.com), append **&features=uncachedVerticals** to the Work vertical URL to view the verticals immediately.

> [!NOTE]
> Added verticals will not be visible on [SharePoint](https://sharepoint.com/) and [Office](https://office.com) when viewed from mobile web browsers.

## Troubleshooting

Here's a list of common issues you might encounter and actions to fix them.

|Error  |Action  |
|---------|---------|
| I see a "Something went wrong" error message on the vertical. | Both the vertical and result types are needed to complete the setup. Make sure you have created both for the same content source. |
| I don't see my result layout, although I created one. | It takes a few minutes because these settings are generally cached. Wait for a few minutes and try again.        |
| I don't see any content sources on the vertical or result type page. | Make sure you have configured connectors and indexed data.   |

## Next steps

[Manage result types](manage-result-types.md)
[Customize the results layout](customize-results-layout.md)
