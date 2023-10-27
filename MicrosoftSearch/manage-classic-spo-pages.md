---
title: "Classic pages in SharePoint Online and Microsoft Search"
ms.author: keremy
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
description: "Using Microsoft Search on classic SharePoint pages"
ms.date: 12/14/2020
---

# Classic pages and Microsoft Search

SharePoint sites created prior to modern sites use a classic search box and classic search results experience. We'll be rolling out a feature that will default classic pages to start using the modern search experience that uses Microsoft Search, which provides personalized results with higher relevance.

Using Microsoft Search is recommended for all sites, including classic, but if your classic sites use custom master pages and/or you have customized your classic search results experience, we'll autodetect these customizations and not switch to Microsoft Search.

## Classic sites that will automatically switch to Microsoft Search

Classic sites will start using Microsoft Search if all of the following are true:

* The site is based on the team site template (like STS#0 and STS#1).
* The site doesn't have the publishing feature turned on.
* The site doesn't use a custom master page (a different master page than oslo.master or seattle.master).
* There are no active query rules other than those adding promoted results for the site, site collection or tenant on the default result source.
* There are no custom result types for the site or the site collection on the default result source.
* The site or the site collection isn't opted out of the switch using the *SearchBoxInNavBar* setting described below.

After the switch to Microsoft Search, classic pages in the site will start to show the search box in the suite navigation bar and remove the classic search box from the page. Then, when a user searches for a term, the results will be displayed using the modern search experience of Microsoft Search.

## Staying with the classic search experience

If your site meets the criteria listed above, but you don't want it to switch to the Microsoft Search experience, you can opt out using the following commands, as the site or site collection owner.

You can use this command at any time, before or after the switch happens, so it's easy to go back to the search experience you had previously.

To run the commands below, you'll use PowerShell with SharePoint PnP PowerShell extensions. You can install and learn more about how to get started [here](/powershell/sharepoint/sharepoint-pnp/sharepoint-pnp-cmdlets). You'll sign in to your site or site collection using this command:

```powershell
Connect-PnPOnline -Url <yoursiteurl> -UseWebLogin
# this will prompt you to sign in to your site. Use the site owner credentials.
```

To stay with classic search experience for a site, run the following command:

```powershell
Set-PnPSearchSettings -Scope Web -SearchBoxInNavBar ModernOnly
# ModernOnly | Inherit
```

Alternately, if you want to set it for all the sites in a site collection, you can use this command:

```powershell
Set-PnPSearchSettings -Scope Site -SearchBoxInNavBar ModernOnly
# ModernOnly | Inherit
```

## Opting into Microsoft Search

For those sites that don't meet the criteria listed above, or for specific sites in a site collection that opted to stay in classic, you can manually enable the Microsoft Search experience.

To change this setting for a specific site, you can use this command:

```powershell
Set-PnPSearchSettings -Scope Web -SearchBoxInNavBar AllPages
# AllPages | Inherit
```

If you want to set it for all the sites in a site collection, you can use this command:

```powershell
Set-PnPSearchSettings -Scope Site -SearchBoxInNavBar AllPages
# AllPages | Inherit
```

> [!NOTE]
> You can manually enable Microsoft Search only for a Team Site or Publishing Site (template ids that contain "STS", "CMSPUBLISHING", "BLANKINTERNET" and "GROUP").
