---
title: "Add a search box to your intranet site"
ms.author: dawholl
author: dawholl
manager: kellis
ms.date: 10/31/2018
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Priority
search.appverid:
- BFB160
- MET150
- MOE150
ms.assetid: f980b90f-95e2-4b66-8b21-69f601ff4b50
ROBOTS: NOINDEX
description: "Get relevant search suggestions and find work results faster by adding a Microsoft Search search box to an intranet site or page."
---

# Add a search box to your intranet site

> [!IMPORTANT]
> This article applies to the Microsoft Search in Bing admin portal. We’re moving the portal to the Microsoft 365 admin center, and then it will be removed. We recommend that you use the Microsoft 365 admin center to get started. [Overview of Microsoft Search](overview-microsoft-search.md).
    
For fast access to relevant search suggestions and work results, add a Microsoft Search search box to any intranet site or page.
  
## Add a search box to an intranet page

You need to add two elements to the page: a container for the search box and the script that powers it.
  
```html
<div id="bfb_searchbox"></div>
<script>
    var bfbSearchBoxConfig = {
        containerSelector: "bfb_searchbox"
    };
</script>
<script async src="https://www.bing.com/business/s?k=sb"></script>
```

On a SharePoint classic site, add a Script Editor Web Part and drop the script in it.
  
## Enable the search box for mobile

For intranet sites or pages available to mobile users, add isMobile: true to the settings object:
  
```html
<div id="bfb_searchbox"></div>
<script>
    var bfbSearchBoxConfig = {
        containerSelector: "bfb_searchbox", 
        isMobile: true
    };
</script>
<script async src="https://www.bing.com/business/s?k=sb"></script>
```

## Put focus on the search box by default

To help users search faster, when the page or site loads place the cursor in the search box by adding focus: true to the settings object:
  
```html
<div id="bfb_searchbox"></div>
<script>
    var bfbSearchBoxConfig = {
        containerSelector: "bfb_searchbox",
        focus: true
    };
</script>
<script async src="https://www.bing.com/business/s?k=sb"></script>
```

## Customize the appearance of the search box 

To help the search box better fit with the style of your intranet, there are a variety of configuration options you can use. Mix and match options to suit your needs.

```html
<div id="bfb_searchbox"></div>
<script>
    var bfbSearchBoxConfig = {
        containerSelector: "bfb_searchbox",
        width: 560,                             // default: 560, min: 360, max: 650
        height: 40,                             // default: 40, min: 40, max: 72
        cornerRadius: 6,                        // default: 6, min: 0, max: 25                                   
        strokeOutline: true,                    // default: true
        dropShadow: true,                       // default: true
        iconColor: "#067FA6",                   // default: #067FA6
        companyNameInGhostText: "Contoso"       // default: not specified
                                                // when absent, ghost text will be "Search work and the web"
                                                // when specified, text will be "Search the web and [Contoso]"
    };
</script>
<script async src="https://www.bing.com/business/s?k=sb"></script>
```

## Use an iFrame to embed a search box

If embedding a script isn't an option for the site, use an iFrame to add the search box. You won't be able to customize the appearance of the search box.
  
```html
<iframe width="564" height="400" src="https://www.bing.com/business/searchbox"></iframe>
```