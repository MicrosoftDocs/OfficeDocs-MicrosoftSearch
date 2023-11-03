---
title: "Customize address bar shortcuts for Microsoft Edge"
ms.author: davidedwards
author: dawholl
manager: kellis
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
ms.date: 03/15/2022
search.appverid:
- BFB160
- MET150
- MOE150
description: "Add custom Microsoft Edge shortcuts for Microsoft Search in Bing or turn off these shortcuts for your organization"
---
# Customize address bar shortcuts for Microsoft Edge

Help your users stay focused and find work results faster when searching from the Microsoft Edge address bar. Two shortcuts are enabled by default, 'work' and your organization's preferred or shortened name. In the Microsoft Edge address bar, users can type a keyword, then press the Tab key. The address bar will indicate they're searching within your organization. When they type their search and press the Enter key, they'll see a search results page with relevant answers and results. You can add two custom shortcuts keywords.

:::image type="content" alt-text="Animated GIF of entering work keyword and using Microsoft Edge shortcut to search work." source="media/edge-shortcuts/microsoft-edge-address-bar-shortcut.gif" lightbox="media/edge-shortcuts/microsoft-edge-address-bar-shortcut.gif":::

> [!NOTE]
> This article applies to Microsoft Edge version 96 or later.

## Manage shortcuts and keywords

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to [Configurations](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/configurations).
2. Under Microsoft Search in Bing shortcut, select **Change**.
3. In the panel, **Enable the Microsoft Search in Bing shortcut** is selected by default. To disable these shortcuts, clear the check box.
4. In Search Keywords field, enter one or two more keywords. You can include spaces and special characters.
5. Select **Save**.

## Frequently asked questions

**Q: The keywords don't work. What's wrong?**

**A:** In the Microsoft Edge address bar, enter edge://settings/search to go to your search settings. Verify that **Show me search and site suggestions using my typed characters** is enabled. You can also use Microsoft Edge group policy to enable search suggestions. To learn more, see [SearchSuggestEnabled](/deployedge/microsoft-edge-policies#searchsuggestenabled).

**Q: Do these shortcuts only support English keywords?**

**A:** No. For localized keywords, you'll need to add the language-specific keyword in the Search Keywords field.

**Q: How long does it take for new keywords to be recognized as shortcuts?**

**A:**  It takes up to two days for Microsoft Edge to recognize custom keywords as a shortcut.

**Q: Can I add shortcuts for my Google Chrome users?**

**A**: Not through the Microsoft 365 admin center. Users can create their own shortcuts in Chrome by going to settings for Manage search engines, and under Other search engines, adding a site name, keyword, and Query URL.

**Q: Can I use these same keywords when using Windows Search?**

**A**: No, only Microsoft Edge supports these keywords shortcuts.
