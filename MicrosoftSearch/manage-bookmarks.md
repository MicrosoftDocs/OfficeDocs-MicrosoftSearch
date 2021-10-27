---
title: "Manage bookmarks"
ms.author: dawholl
author: dawholl
manager: jeffkizn
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
search.appverid:
- BFB160
- MET150
- MOE150
ms.assetid: c0c814d0-f7e4-444e-b18e-09beb45c9322
description: "Create and update bookmarks and ways to bulk edit bookmark results for Microsoft Search"
---
# Manage bookmarks

Bookmarks help people quickly find important sites and tools with just a search. Each bookmark includes a title, URL, a set of user-friendly keywords to trigger the bookmark, and a category.

## What makes a great bookmark

A great bookmark has four key elements:

1. A strong, informative **title**. Aim for no more than eight words or about 60 characters maximum. You want your users to click on the title and view the content, but avoid obvious clickbait:
    - Good: Try this week’s tasty favorites from the cafeteria menu. Title is clear, concise, and interesting, but could be overpromising.
    - Better: This week’s cafeteria menu. Doesn't overpromise or sound like an ad.
    - Avoid: You won’t believe what’s coming to the cafeteria menu this week. Uses clickbait clichés that sound like an ad.
2. A succinct **description**, about 300 characters, that summarizes the purpose or functionality of the linked resource.
3. A collection of **keywords** that will help people find the bookmark when they search. We suggest a minimum of at least five keywords. Also, include variations that people in your organization might use, for example, dining menu, lunch menus, and café menu could all be variations for cafeteria menu.
4. A helpful set of **categories** that make it easier to sort and filter bookmarks in the admin center. Your users never see the assigned categories.

## Create bookmark answers

In the [Microsoft 365 admin center](https://admin.microsoft.com/), go to [Bookmarks](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/bookmarks) and choose how you want to create new bookmarks:

- Add bookmarks
- Import SharePoint results
- Add default bookmarks and suggested bookmarks
- Import bookmarks
- Publish or review recommended bookmarks

### Add bookmarks

Search admins and editors can add bookmarks in the Microsoft 365 admin center and either publish or save them to draft. Publishing a bookmark immediately refreshes the search index, making it discoverable to users right away. You can also schedule a bookmark by specifying the date and time it will be published.

- **Published**: Bookmarks are available to the organization’s users through Microsoft Search.
- **Draft**: Bookmarks saved as drafts aren't available to your users. Use this status if you or other stakeholders want to review or update bookmarks before publishing them.
- **Scheduled**: Bookmarks that will be published on the specified date and time.

You can use the Microsoft Search content creator browser extension to easily add bookmarks. Just go to the site you want to add as a bookmark, and click Add in the extension. To install the extension for Microsoft Edge or Google Chrome, go to the [Chrome web store](https://chrome.google.com/webstore/detail/microsoft-search-content/nocnablpaoeecfmfnjoheefkogmleipm) and add it to your browser.

### Import SharePoint results

If your organization set up Promoted Results in SharePoint, you can import the titles, URLs, and descriptions from the Promoted Results for your tenant into Microsoft Search and make the imported content available to your users. In most cases, importing SharePoint results takes just a few minutes. If you're importing a large number of results, it may take up to 48 hours. This is an easy way to quickly populate search results and make it more effective for your users. We recommend using promoted results from SharePoint as a reference to understand how to name and create relevant search results.

### Add default and suggested bookmarks

We've included some default suggested bookmarks that your users may find helpful, including bookmarks for HR, benefits, IT support, password management and more. Review, update, and publish these suggested bookmarks to provide high-quality results to your users right away.

Your users can also suggest bookmarks that would like to see added using feedback links in Microsoft Search. Their recommendations will appear as suggested bookmarks.

### Import bookmarks

Use the Import feature to make adding or editing a large number of bookmarks faster and easier. Use it to:

- Bulk add bookmarks: Add details in the bookmark template file, and then import it.
- Bulk edit bookmarks: Export bookmarks to a .csv file, edit the bookmark details in the exported file, and then import the edited file.

A few important points about the template file:

- Never edit data in these fields: *ID*, *Last Modified*, and *Last Modified By*
- If you include the *ID* of an existing bookmark, it will be replaced with the information in the import file.
- For existing bookmarks with the same title or URL, the bookmark will be updated with information in the import file.
- Not all fields in the template file are required and required fields vary depending on the bookmark state.
- Based on the *State* field, bookmarks will be saved as draft, suggested, scheduled, excluded, or they'll be published automatically.
- For partners who manage multiple organizations, you can export your bookmarks from one org and import them into another. But you must remove the data in the *ID* column before you import.

### Prevent import errors

You'll get an error if any required data is missing or invalid, and a log file is generated with more information about the rows and columns to be corrected. Make necessary edits and try importing the file again. You can't import or save any bookmarks until all errors are resolved.

To prevent errors, make sure your import file is properly formatted and:

- Includes the header row and all the columns that were in the import template
- The column order is the same as the import template
- All columns have values, except the three that can be empty: *ID*, *Last Modified*, and *Last Modified By*
- The *State* column isn't empty, it's required information
- When importing Published, Suggested, Scheduled, or Draft bookmarks, the *Title*, *URL*, and *Keywords* columns are required
- When importing Excluded bookmarks, the *URL* column is required

To prevent bookmark-to-bookmark duplication errors:

- Don't use duplicate URLS for different bookmarks. If a URL is assigned to another bookmark and you try to add it again from an import file, you'll get an error. This also applies to duplicate URLs for other types of answers.
- When updating existing bookmarks, use the *bookmark ID* column. You can update any other property of an existing bookmark, such as keyword or description, but you should make sure the *bookmark ID* is in the appropriate column of the import file. If the *bookmark ID* is present, it won't be treated as new addition and won't be processed as an error.

### Publish or review recommended bookmarks

To reduce the manual effort required to add bookmarks, Microsoft Search can evaluate your organization's SharePoint links and recommend bookmarks. You can review them before publishing or set them to automatically publish. No setup is needed for recommended bookmarks, they're enabled and set to autopublish by default. To change these settings at any time, select **Manage bookmarks** to open the Bookmark settings panel.

![Screenshot of Recommended bookmark settings in the Microsoft 365 admin portal.](media/bookmarks-recommendedsettings.png)

If recommended bookmarks are enabled, the recommendation engine will evaluate SharePoint sites in your organization to identify high-traffic links. After an initial evaluation period, the recommended bookmarks will either be autopublished or added to the list of suggested bookmarks. The next cycle—a 30-day evaluation period followed by autopublishing or adding suggested bookmarks—will then begin.

We suggest Search admins or editors review these autopublished or suggested bookmarks regularly. Also, recommended bookmarks will never include URLs found in existing Published, Suggested, Scheduled, or Excluded bookmarks.

To ensure only users with access will see a recommended bookmark in work results, an access check feature is included for all recommended bookmarks. Users will never see a recommended bookmark for a SharePoint site they can't access. This access check is controlled by the option **Only people with access to this link** in the Groups setting for each recommended bookmark.

The access check will stop if the URL in the recommended bookmark or the Groups setting is changed.

To prevent the recommendation engine from publishing or suggesting a bookmark to a particular site, you can add the URL to an excluded list. The recommendation engine will never publish or suggest a bookmark for an excluded site or a page within an excluded site.

## About keywords and reserved keywords

A bookmark can have several keywords and share the same keyword, but reserved keyword can't be shared. A reserved keyword is a unique term or phrase that triggers one specific bookmark. A reserved keyword can be associated with one answer only. Use reserved keywords sparingly.

## Frequently asked questions

**Q: How long does it take for a bookmark to be visible in Microsoft Search after it's published?**

**A:**  A bookmark is available in Microsoft Search immediately after publishing.

**Q: How long does it take for a recommended bookmark to appear?**

**A:**  Recommended bookmarks will only appear in Microsoft Search if both Recommended bookmarks and autopublishing are enabled. During the initial evaluation period, the recommendation engine will evaluate SharePoint traffic to identify suitable bookmarks and then autopublish them. Once published they become available immediately in Microsoft Search.

**Q: How long does it take for a deleted bookmark to be removed from Microsoft Search results?**

**A**: Deleted bookmarks are immediately removed from work results.

**Q: Will Microsoft Search recommend bookmarks from sites in all languages?**

**A**: Yes, Microsoft Search can recommend bookmarks from any internal SharePoint site, regardless of the language.

**Q: Can I stop showing recommended bookmarks in search results?**

**A:** To stop showing recommended bookmarks, turn the autopublish setting off in your admin center. Recommended bookmarks will be added to the list of suggested bookmarks.

**Q: How can I identify a recommended bookmark in search results or the admin center?**

**A:** In search results, recommended bookmarks include the phrase "Suggested for you" before the URL. In the admin center, recommended bookmarks will have an Owner value of "SYSTEM".

**Q: How is access to a recommended bookmark managed?**

**A**: A Microsoft-engineered access engine determines if the bookmark URL is accessible to a particular user and will only show the recommended bookmark to the correct audience. However, if the URL is edited or the Groups setting is changed, the engineered access engine will be disabled.

**Q: What happens if no action is taken on recommended bookmarks added to the Suggested list?**

**A**: To avoid a high volume of bookmarks in the suggested list, a recommended bookmark (owner = SYSTEM) will be purged after 180 days.

**Q: Where do I find the App ID for a Power App?**

**A**: Go to the Power Apps site and view the Details pane for the app. Learn more about [getting an app ID](/powerapps/maker/canvas-apps/get-sessionid#get-an-app-id).
