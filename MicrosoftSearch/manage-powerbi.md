---
title: "Manage Power BI answers"
ms.author: bstucker
author: bstuck
manager: bstucker
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
ms.assetid: c0c814d0-f7e4-444e-b18e-09beb45c9322
description: "Manage how Power BI reports and data appear in search results"
ms.date: 01/04/2021
---

# Manage Power BI answers

To make it easier for your users to find the data and analytics they need to make informed decisions, Microsoft Search has added support for Power BI dashboards and reports. Here are a few of the benefits of Power BI search:

* **Easy to use:** This out-of-box search experience helps users easily and quickly find Power BI dashboards and reports across your organization.
* **Richer content:** To make Power BI search results more useful, they include key information like the type of content—dashboard or report—and the team or person that owns it.
* **Built-in data protection:** Power BI results will only appear for users that have access to the dashboard or report.
* **Unified search experience:** To maintain a cohesive experience, Power BI results are consistent across all search entry points. Wherever you search, you'll get the same results with the same look and feel.

## What users experience

Microsoft Search users can find Power BI results by searching from the Windows search box, SharePoint, Office 365, and Bing. Users can search for reports and dashboards with queries like these:

* Power BI about `<topic>`
* Power BI for `<topic>`
* `<topic>` Power BI dashboard or Power BI dashboard `<topic>`
* `<topic>` Power BI report or Power BI report `<topic>`
* `<topic>` Power BI metrics or Power BI metrics `<topic>`
* `<topic>` Power BI scorecard or Power BI scorecard `<topic>`

Replace `<topic>` in the examples above with the information you're looking for, like sales, usage, capacity, 2021, Q1, and more, to see relevant results from Power BI.

:::image type="content" source="media/powerbi-answers/powerbi-serp.png" alt-text="Screenshot of a SERP with Power BI answers and vertical." border="true":::

## Turn Power BI search on or off

Power BI results are enabled for your organization by default. Your Power BI admin can disable them at any time. In the Power BI Admin portal, go to Tenant settings and disable the **Use global search for Power BI** setting. To learn more, see [Administering Power BI in the admin portal](/power-bi/admin/service-admin-portal#use-global-search-for-power-bi-preview).

:::image type="content" source="media/powerbi-answers/powerbi-admin.png" alt-text="Screenshot of setting to turn Power BI answers on or off." border="true":::

> [!NOTE]
> When using Microsoft Search, your search query and the results returned from Power BI may be processed in a region or geography that's different than where your Power BI tenant data is located.

## Frequently Asked Questions

**Q: Is Power BI search enabled by default?**

**A:** Yes. Power BI search is enabled by default for Microsoft Search. There's no first-time setup required by the tenant admin for this feature.

**Q: Can Power BI search be enabled or disabled for specific groups or users?**

**A:** Currently, it can only be enabled or disabled for your entire organization.

**Q: If Power BI search is disabled, is the Power BI search result page hidden?**

**A:** No. The Power BI search result page will appear with a message informing users that it's not currently available for their organization.

**Q: Will I see the Power BI search result page if I don’t have a Power BI license?**

**A:** No. If a search user doesn’t have a Power BI license, the Power BI search result page won’t appear in Microsoft Search results.

**Q: Will I see Power BI search results that I can't access?**

**A:** No. Microsoft Search will only return Power BI results you have access to.

**Q: Can I customize the Power BI search results (for example, the report type or report owner)?**

**A:** Currently we don’t support customizing the fields included in Power BI search results.