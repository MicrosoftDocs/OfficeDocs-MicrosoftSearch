---
title: "Manage search apps"
ms.author: bstucker
author: bstuck
manager: bstucker
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
ms.date: 10/27/2021
search.appverid:
- BFB160
- MET150
- MOE150
description: "Manage search apps published by your organization's bot developers"
---

# Manage search apps (preview)

The Microsoft Federated Search Platform enables you to surface data in Microsoft Search experiences without merging that information with your Microsoft 365 index. For more information, see [Announcing developer preview of the Microsoft Federated Search Platform](https://techcommunity.microsoft.com/t5/microsoft-search-blog/announcing-developer-preview-of-the-microsoft-federated-search/ba-p/2480763). Using the Microsoft Bot framework, you can show data from custom applications as Search Apps in the search results page.

> [!NOTE]
> Search apps is in preview. To request access, use the [Microsoft Search Developer Preview form](https://aka.ms/SearchDevPrivatePreview). In question 7, select Federated Search.

## Create search apps

A developer in your organization can build a search app and submit  for Search admin’s approval. To learn how to create a search app, see: [Connect a Bot Framework bot to Search](/azure/bot-service/bot-service-channel-connect-search). Once the developer creates a search app and links to the data source, it will be ready for your approval. After the developer submits the app, it will appear in the Search & Intelligence admin center.

## Publish search apps

Search admins and editors can either publish or disable a search app. Publishing a search app immediately makes the results appear in the search results page. Disabling a search app means users in your organization will not see the results from this search app on the search results page.

- **Published state**: Search apps are available to the organization’s users through Microsoft Search.
- **Disabled state**: Search apps saved as disabled state aren't available to your users. Use this status if you or other stakeholders want to review search apps before publishing them.
- **Needs review state**: Search apps submitted by a developer are shown in this state until published or disabled.

A search app can be deleted by a developer at any time. To learn more, see [Connect a Bot Framework bot to Search](/azure/bot-service/bot-service-channel-connect-search).

> [!NOTE]
> The developer documentation also refers to search apps as search provider.

To manage search apps, follow these steps:

1. In the [Microsoft 365 admin center](https://admin.microsoft.com/), go to [Search Apps](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/searchapps).
1. Click the search app name in the list view.
1. Click **Enable answers on search results page** checkbox to allow this search app to display results in the All vertical.
1. Click **Publish** to publish this search app.
1. Click **Disable search app** if you don’t want to see results from this app.
1. To give feedback to the developer on the search app, you can use the **send feedback mail to** link in the detail panel.
