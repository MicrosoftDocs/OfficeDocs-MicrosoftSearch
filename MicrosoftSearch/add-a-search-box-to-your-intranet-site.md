---
title: "Add a search box to your intranet site"
ms.author: kellis
author: kellis
manager: kellis
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
ms.assetid: f980b90f-95e2-4b66-8b21-69f601ff4b50
ROBOTS: NoIndex
description: "Get relevant search suggestions and find work results faster by adding a Microsoft Search search box to your intranet site or page."
ms.date: 01/08/2019
---

# Add a search box to your intranet site

To provide your users with easy access to results from your organization, add a Microsoft Search in Bing search box to any intranet site or page. These are some of the benefits:

- A search box on your intranet portal provides a familiar, trusted entry point to start searching
- Can be added to your SharePoint (classic and modern), SalesForce, Confluence, and other intranet pages and sites
- Supports all major web browsers, including Google Chrome and Microsoft Edge
- Only search suggestions from your organization appear, web suggestions are never included
- Takes users to a Microsoft Search in Bing work results page, which excludes ads and web results
- You control the appearance and behavior of the search box, including the ability to land users on a default vertical or a custom vertical you've created

> [!NOTE]
>To see search suggestions, users must be signed in to their Microsoft Entra account. Users that aren't signed in will be prompted to do so after they enter a query.

If you have questions or comments about adding or using an embedded search box, share them with us at [aka.ms/ESB](https://aka.ms/ESB).
  
## Add a search box to a SharePoint or intranet page

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

For SharePoint classic or modern pages, download bing-search-box.sppkg from the [Microsoft Search public repro](https://github.com/microsoft-search/bing-search-box/releases), deploy it to your SharePoint app catalog, then add the app to your SharePoint sites. For details, see [Deploy your client-side web part to a SharePoint page](/sharepoint/dev/spfx/web-parts/get-started/serve-your-web-part-in-a-sharepoint-page#deploy-the-helloworld-package-to-app-catalog).

## Add a search box to your Confluence page

On the Confluence page, select **Edit**, add an iFrame widget with these parameters, and Publish. 
- URL: `https://www.bing.com/business/searchbox`
- Title: `Org-Name search` or `Workplace search`
- Width: `560`
- Height: `200`

## Add a search box to your SalesForce Home page

In your Visualforce Pages, create a new view and add the code in the Markup section.

1. Log in to your SalesForce account as an admin and select **Setup** in the upper-right corner to open a Setup page.
1. On the left side panel, select **Platform Tools** > **Custom Code** > **Visualforce Pages**.
1. Create a new View and enter a name for it. In the Restrict Visibility section, set **Visible to all users**.
1. Save your view.
1. In the middle of your view, select **New** to open Page Edit. Enter a label, a name, and select the **Available for Lightning Experience, Experience Builder sites, and the mobile app** check box.
1. In the Visualforce Markup section, add this code and **Save**.

```html
<apex:page >
    <iframe width="500" height="300" src="https://www.bing.com/business/searchbox"></iframe>
</apex:page>
```

You can also customize the height and width of the search box with this code

```html
<apex:page >
  <div style="height:400px;">
  <div id="bfb_searchbox"></div>
  <script>
      var bfbSearchBoxConfig = {
          containerSelector: "bfb_searchbox",
          width: 400,
          strokeOutline: true
      };
  </script>
  <script async="async" src="https://www.bing.com/business/s?k=sb"></script>
  </div>
</apex:page>
```

To add the Visualforce component to your SalesForce homepage:
1. Go to your SalesForce homepage, `https://Instance-Name.lightning.force.com/lightning/page/home`.
1. Select the Gear icon, then **Edit Page**.
1. Select the + (plus) icon anywhere on the Homepage to add the Visualforce component there.
1. On the left side, select Visualforce. On the right side, select the Visualforce Page Name you created earlier.
1. Add a label and **Save**.
On your SalesForce Homepage, the search box you created should appear.
  
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

To help the search box better fit with the style of your intranet, there are various configuration options you can use. Mix and match options to suit your needs.

```html
<div id="bfb_searchbox"></div>
<script>
    var bfbSearchBoxConfig = {
        containerSelector: "bfb_searchbox",
        width: 560,                             // default: 560, min: 360, max: 650
        height: 40,                             // default: 40, min: 40, max: 72
        cornerRadius: 6,                        // default: 6, min: 0, max: 25                                   
        strokeOutline: true,                    // default: true
        dropShadow: true,                       // default: false
        iconColor: "#067FA6",                   // default: #067FA6
        title: "Search box",                    // default: "Search box"
        vertical: "Person-people",              // default: not specified, search box directs to the All vertical on the WORK results page
        companyNameInGhostText: "Contoso"       // default: not specified
                                                // when absent, ghost text will be "Search work"
                                                // when specified, text will be "Search <companyNameInGhostText>"
    };
</script>
<script async src="https://www.bing.com/business/s?k=sb"></script>
```

## Direct users to a default or custom vertical

To provide easy integration between your line-of-business apps or intranet sites and your work results, you can also specify a default or custom vertical users should land on when they select a search suggestion.

Use the vertical option in bfbSearchBoxConfig to define the vertical you want. For example, if you want users to always land on the Sites vertical, one of the default verticals, use the value "Site-sites".

:::image type="content" alt-text="Screenshot of work results page on Microsoft Search in Bing showing the Sites vertical results and URL." source="media/sites-vertical-esb.png" lightbox="media/sites-vertical-esb.png":::

For custom verticals, use the hash at the end of the URL. You can find these values by searching from the work page on Bing, clicking a vertical label, and copying the value after the number sign (#).

:::image type="content" alt-text="Screenshot of work results page on Microsoft Search in Bing showing a custom Presentation vertical results and URL." source="media/custom-vertical-esb.png" lightbox="media/custom-vertical-esb.png":::

## Use an iFrame to embed a search box

If embedding a script isn't an option for the site, use an iFrame to add the search box. You won't be able to customize the search box.
  
```html
<iframe width="564" height="400" src="https://www.bing.com/business/searchbox"></iframe>
```

## InPrivate mode and Conditional Access

An embedded search box will be disabled if the page or site is opened in an InPrivate window. Also, with Microsoft Entra Conditional Access support in Microsoft Edge, Bing.com doesn't support Microsoft Entra sign-in when using InPrivate mode. For more information about Conditional Access in Microsoft Edge, see [Microsoft Edge and Conditional Access](/deployedge/ms-edge-security-conditional-access#accessing-conditional-access-protected-resources-in-microsoft-edge).
