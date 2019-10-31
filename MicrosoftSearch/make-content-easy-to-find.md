---
title: "Make content easy to find with Microsoft Search"
ms.author: anfowler
author: adefowler
manager: mnirkhe
ms.date: 10/30/2019
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Create bookmarks, locations, and Q&A items to make your organization's content easy to find."
---
# Make content easy to find

Microsoft Search helps users find relevant content. It's a secure way to search both your intranet and web content. This type of integration across the web and organizations is only available from Microsoft. 

Search administrators use their knowledge of an organization to make it easy for users to find relevant content. 

## Identify the information your users need
To find out what your users need and make that information easily discoverable, try some of these methods:

- Use intranet search logs to determine sites and pages that get the most traffic.
- Determine apps, sites, and tools that are used on a daily or weekly basis.
- Find direct links for employee benefits.
- Find policies and processes that users need to be aware of.
- Decide who users contact for support and how they do that.
- Get information that's needed on a recurring basis, either seasonally or based on business cycles. An example is people looking for tools to book time off or quarterly financial updates.
- Collect policies for regional or mobile users. Examples are benefits that vary by location.
- Determine internal sites and information for common web searches. Examples are traffic, public transit information, local weather, discounts available from corporate partners, and health and fitness programs.
- Find information about company-sponsored events, conferences, or retreats.
- Research common IT, HR, and support issues and frequently asked questions (FAQs) and answers.

## Leverage subject mattmr experts (SMEs) and users
In an organization, users search for a range of simple to complex topics. Simple examples are office addresses and employee benefits. Complex examples are new work processes, technical information, and how-to-do content. To create or find such a wide variety of content, you need expertise in different fields, subjects, and technologies. Most search administrators don't have specific knowledge on every subject. To scale the amount of available content without outside resources, seek expertise and knowledge from others in your organization.

### Leverage SMEs
Leverage the SMEs in your organization including experts from HR, support, sales, technology, and other key areas. SMEs can contribute content directly if you add them as Microsoft Search editors. 

### Involve your users
Ask users to suggest resources to bookmark. Also ask users to report errors like broken or invalid links.

## Make content easy to find 
In Microsoft Search, administrators create [bookmarks](manage-bookmarks.md), [Q&A](manage-qas.md), [Locations](manage-locations.md), and [PowerApps](integrate-powerapps.md) that make content easier to find. Each of these search components includes a title, a URL, and a set of keywords that trigger it.

### Titles and descriptions
Connected titles and descriptions help users determine whether or not results answer their search query. Good titles and descriptions reflect the core purpose of the result. An example is the title **Childcare benefits** with the description *Learn about benefits to help pay childcare costs*. With this connected data, users who search for **childcare** can find monetary support benefits and get a link to find out more.

### Keywords
With keywords, users in your organization can search and find relevant content. You need to associate keyword terms with their related search results. Microsoft Search suggests keywords based on the title and URL of your content. To identify more keywords, get answers to these questions:

1. **What search terms can find the information you identified?** Refer to any existing terminology in your organization, as well as related variations, acronyms, subjects, and topics.
1. **What variations or words do people use to talk about this information?** Ask your support team to provide these keywords.

For example, if you create a result that links to a tool for submitting vacation requests, keywords **vacation** and **submit vacation request** are good options to include. Users in your organization might also search for vacation-related information with **holiday** or **time off**. To make it easier for users to find relevant content, add those keywords and others like **submit holiday request** and **request time off**.

### Reserved keywords
 A reserved keyword is a unique term or phrase that triggers a result. Unlike other keywords, reserved keywords are associated with one result only. Use reserved keywords sparingly to allow Microsoft Search to learn based on usage.

An example is a bookmark for a site for submitting your hours. If **log time** is a reserved keyword, users in your organization who search for **log time** see that site as the only bookmark in the Microsoft Search box. 

### Group related content with keywords
If you want users to find sets of related content when they search for a specific term, assign the same keyword to all related content. An example is a search for processes and tools around life status changes. To group answers together on updating benefits, tax information, and name and alias changes, include a keyword like **marriage**.

### Search settings
With search settings, you can tailor your content and target specific groups of users. These Microsoft Search settings control when a search result appears and who can see it:

- **Dates:** To control when content is available or unavailable, set a start date and an end date. For example, time-sensitive material appears in search result when it's relevant.
- **Country/region:** You can select countries or regions, so only users in those locations see certain content. For example, country-specific information appears in search results in those countries only.
- The **Groups** settings make results available only to members of selected groups. For example, if you create sites that relate only to employees in the HR department, map this setting to the appropriate HR security group.
- **Device & OS:** Select device types or operating systems, so only users who search on those devices or use those systems see that bookmark.
- **Targeted variations:** This setting varies the content of a bookmark based on a user's device and location.

## Test your content
After you create [bookmarks](manage-bookmarks.md) and [Q&A](manage-qas.md), verify these results:
- The correct bookmark or QA appears.
- All content grouped together with keywords appears together as planned.
- Nothing unexpected appears in search answers.
- The bookmark or Q&A has enough information.

Users and SMEs who contribute to content creation can help test and validate search results.

## Review and update periodically
Authoritative information like [bookmarks](manage-bookmarks.md) and [Q&A](manage-qas.md) need to stay fresh. Take these steps regularly:
- Fix or remove broken and invalid URLs.
- Remove bookmarks or Q&A that are no longer relevant.
- Check for tool, site name, or team name changes.
- Consider whether the bookmark or Q&A is authoritative enough or needs a clearer description.

## Bookmarks
You can create a [bookmark](manage-bookmarks.md) in just a few steps. Each bookmark includes a title, a URL, and a set of keywords that trigger it. A bookmark can have several keywords, and several bookmarks can share the same keyword. But reserved keywords can't be shared. When you create or modify a bookmark, the search index refreshes, and the bookmark is available to users immediately.

If your organization has **promoted results** set up in [SharePoint](http://sharepoint.com/), you can import those results into Microsoft Search. With promoted results, you can quickly populate search results, make the content available to users, and make Microsoft Search more effective as soon as you set it up. We recommend that you use promoted results from SharePoint as a reference to understand how to name and create relevant search results. 

### Add or edit a single bookmark
1. Go to the Microsoft 365 [admin center](https://admin.microsoft.com).
1. In the navigation pane, go to **Settings**. Then select **Microsoft Search**. The **Bookmarks** tab is selected by default.
1. To add a bookmark, select **Add new**. 
1. To edit a bookmark, select the bookmark in the relevant bookmark list. 
1. As you add or edit the information, the preview automatically updates.

### Add or edit bookmarks by using browser extensions
Search administrators can create search content easily by using browser extensions. To add the site as a bookmark, install the browser extension. Then go to the site and add it as a bookmark. To learn more, see [Manage bookmarks](manage-bookmarks.md).

Currently, browser extensions are available for [Microsoft Edge](https://www.microsoft.com/windows/microsoft-edge) and [Google Chrome](https://www.google.com): 
- To download the Edge extension, go to the [Microsoft Store](https://www.microsoft.com/p/microsoft-search-content-creator/9nrqdbcbwq55?activetab=pivot:overviewtab).
- To download the Chrome extension, go to the [Chrome web store](https://chrome.google.com/webstore/detail/microsoft-search-content/nocnablpaoeecfmfnjoheefkogmleipm).

### Bulk add or edit bookmarks
With the **import** and **export** features, search admins can bulk create or edit [bookmarks](manage-bookmarks.md). This feature is helpful when an administrator wants to add or edit a large number of bookmarks. 

The import and export features provide these functions:
- **Bulk add bookmarks**. Add details in the bookmark template file and then import it.
- **Bulk edit bookmarks**. Export bookmarks to a CSV file, then edit the bookmark details in the exported CSV, and then import the updated CSV.
- **Import promoted sites from [SharePoint](http://sharepoint.com/)**.
- **Backup bookmarks**. Export bookmarks to a CSV file.

To import or export bookmarks, take these steps:
1. In the upper-right corner of the **Bookmarks** tab, select **Import**. 
1. To download all the existing bookmarks in a CSV file, select **Export**.
1. In the right pane, choose the option to import by using a CSV file or from [SharePoint](http://sharepoint.com/).
1. To get a list of the required fields and details, download the template file. 
1. Add or edit bookmark details in the template file. Then save it on your computer. 
1. In the **Import bookmarks** pane, select **Browse**. Then select the CSV file you want and select **Import**.

### Template guidelines
Be aware of these guidelines and restrictions when you work with template files:
- Never edit data in these fields: *Id*, *Last Modified*, and *Last Modified By*.
- If you include the *Id* of an existing bookmark, it's replaced with the information in the import file.
- If there's a bookmark with the same title or URL in the existing file, the bookmark is updated with information in the import file.
- Not all fields in the template file are required, and required fields vary depending on the bookmark state.
- Based on the *State* field, bookmarks are saved as **draft**, **suggested**, or **scheduled**. Otherwise, they're published automatically.
- If you manage multiple organizations, you can export your bookmarks from one org and import them into another. But you must remove the data in the *Id* column before you import.

#### Prevent import errors

You get an error if any required data is missing or invalid. A log file generates with more information about the rows and columns to be corrected. Make necessary edits and try importing the file again. You can't import or save any bookmarks until all errors are resolved.

To prevent errors, make sure your import file is properly formatted and meets these requirements:
- The header row and all the columns in the import template are included.
- The column order is the same as the import template.
- All columns have values, except the three that can be empty: *Id*, *Last Modified*, and *Last Modified By*. 
- The *State* column isn't empty.

### PowerApps

By adding existing [PowerApps](integrate-powerapps.md) to your bookmarks, users can complete tasks like entering vacation time or reporting expenses. 

#### What are PowerApps?

With the PowerApps service, you can build business apps that run in a browser or on a phone or tablet. No coding experience is required. PowerApps work in any browser and on any device. They take less than a minute to add. To learn more about PowerApps, see these articles:
- [Guided learning](https://docs.microsoft.com/learn/browse/?products=powerapps)
- [PowerApps documentation](https://docs.microsoft.com/powerapps/maker/canvas-apps/get-sessionid)
- [PowerApps home](https://make.preview.powerapps.com/environments/839eace6-59ab-4243-97ec-a5b8fcc104e4/home)

#### Add a PowerApp to a bookmark

1. Find the [App ID](https://docs.microsoft.com/powerapps/maker/canvas-apps/get-sessionid#get-an-app-id) for the PowerApp that you want to add.
1. Sign in and go to the Microsoft 365 [admin center](https://admin.microsoft.com).
1. In the navigation pane, go to **Settings**. Then select **Microsoft Search**.
1. Add a bookmark or find an existing bookmark that you want to add a PowerApp to.
1. In **Bookmark settings**, select **Power App**. Then select **Add a Power App**.
1. Enter the **App ID**. The height and width adjust automatically. Bookmarks can support both portrait and landscape orientations, but currently the size can't be changed. To make it easy to test, the bookmark preview shows a fully functional PowerApp .
1. Select **Publish** or **Save to Draft**.

## Q&A

Creating a [Q&A](manage-qas.md) is like creating [Bookmarks](manage-bookmarks.md). With Q&A, you can provide answers to users questions instead of just a link to webpage. You can format answers in rich text by using available tools. If a bookmark and a Q&A share the same keyword, the bookmark result shows first. Like bookmarks, the Q&A index refreshes immediately after you add or change a Q&A. 

### Add or edit a single Q&A

Take the same steps for [Q&A](manage-qas.md) that are described for [Bookmarks](manage-bookmarks.md) in [Add or edit a single bookmark](#add-or-edit-a-single-bookmark).

#### Supported HTML tags

You can use HTML content or add HTML tags to your answer, or description. We support these HTML tags:
 
- blockquote
- div
- em
- h1, h2, h3, and h4
- ol, ul, and li
- p
- pre
- span
- strong
- table, thead, tbody, tr, th, and td
- u
- a
- code
- br
- hr
- img

Unsupported tags are either ignored or displayed as text. Make sure you preview your cards.

### Bulk add or edit Q&A

Administrators can use the **import** and **export** features to bulk create or edit [Q&A](manage-qas.md). This feature is helpful when administrators need to add or edit a large number of Q&A. 

The **import** and **export** features provide the same functions as described in the [Bulk add or edit bookmarks](#bulk-add-or-edit-bookmarks) section except that you can't **Import promoted sites from [SharePoint](http://sharepoint.com/)**. 

To import or export Q&A, take the same steps as described in the [Bulk add or edit bookmarks](#bulk-add-or-edit-bookmarks) section. Go to the **Q&A** tab instead of the **Bookmarks** tab.

Review the [guidelines and restrictions](#template-guidelines) for template files.

> [!Note]
> You can't import Q&A items if there are errors in the template file. To prevent errors, make sure your import file is properly formatted and it includes all the required information. See more information on how to [prevent import errors](#prevent-import-errors).

## Locations

With [Locations](manage-locations.md), your users can find addresses and locate your organization's buildings. The **Locations** feature provides an accurate location for offices, campuses, and buildings as well as directions and navigation. Fpr best results, administrators need to add all the important locations of their organizations to Microsoft Search. Unlike [Bookmarks](manage-bookmarks.md) and [Q&A](manage-qas.md), the Locations index doesn't refresh immediately. It can take several hours for new or changed locations to appear in search results.

### Add or edit a single location

Take the same steps for [Locations](manage-locations.md) that are described for [Bookmarks](manage-bookmarks.md) in [Add or edit a single bookmark](#add-or-edit-a-single-bookmark).

### Bulk add or edit locations

Administrators can use the **import** and **export** features to bulk add or edit locations. These features are helpful when administrators need to add or edit a large number of locations. 

The **import** and **export** features provide the same functions as described in the [Bulk add or edit bookmarks](#bulk-add-or-edit-bookmarks) section except that you can't **Import promoted sites from [SharePoint](http://sharepoint.com/)**. 

To import or export locations, take the same steps as described in the [Bulk add or edit bookmarks](#bulk-add-or-edit-bookmarks) section. Go to the **Locations** tab instead of the **Bookmarks** tab.

Review the [guidelines and restrictions](#template-guidelines) fpr template files.

> [!Note]
> You can't import location items if there are errors in the template file. To prevent errors, make sure your import file is properly formatted and it includes all the required information. See more information on how to [prevent import errors](#prevent-import-errors).

## Review and update Bookmarks, Q&A, and Locations

 Microsoft Search provides usage statistics for [Bookmarks](manage-bookmarks.md), [Q&A](manage-qas.md), and [Locations](manage-locations.md). The statistics provide this data:
 - How users engage with your search results.
 - Whether users find what they look for.
 - Gaps in the available content.
 
With usage statistics, administrators can monitor performance and take appropriate action to fine tune search results. 

### Get details about Bookmarks, Q&A, and Locations

Microsoft Search shows you how many [Bookmarks](manage-bookmarks.md), [Q&A](manage-qas.md), and [Locations](manage-locations.md) are published, scheduled, or suggested. The dashboard shows Bookmark, Q&A, and Location totals by status:

- **Published:** The number of published results that are available to users.
- **Scheduled:** The number of scheduled results in the publish pipeline.
- **Suggested:** The number of suggestions from users.

Suggested [Bookmarks](manage-bookmarks.md), [Q&A](manage-qas.md), and [Locations](manage-locations.md) are a good indicator of gaps in your content. They help you understand what your users look for but don't find. This data might indicate that you need to create more Bookmarks, Q&A, or Locations. Or you might need to update your existing content by using better keywords, reserved keywords, and search strings to make your content more discoverable.

### Review top search queries

To find out which searches generated the most impressions in the last 90 days, review your top search queries. *Impression* means how many times a page was viewed in search results. The **Top Queries** card shows the top 25 user searches for each result type, the total number of searches,and the click-through rate (CTR). With this report, you can identify search query volume and determine queries with high and low search activity.

Low search count might indicate user dissatisfaction. Either users aren't looking for that content, or they're using different keywords to find it. CTR shows how often users select the promoted results and how useful your query rules and results are to users. A low CTR indicates that users find the content, but it doesn't meet their needs. In such cases, review the content. To align content to search queries, make sure it matches users' search and update titles, descriptions, and keywords. 

### Analyze impressions by result type

Easy-to-read graphs in the **Impression Distribution by Result Type** card show impressions over various time frames. The timeline shows the daily number of impressions for a result type. With these graphs, you can determine which result type is most frequently or infrequently used. Infrequent use of a particular result type doesn't necessarily mean that the result type isn't good. It just shows how users are using the search result.

 If a particular result type is preferred by users, you might create more search results of the same types. To ensure that keywords are appropriate, review the keywords of results types with low usage. With this report, you can also see changes in user behavior over a period of time.
