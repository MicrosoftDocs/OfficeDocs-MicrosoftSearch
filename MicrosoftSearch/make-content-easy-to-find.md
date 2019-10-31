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
In Microsoft Search, administrators create [Bookmarks](manage-bookmarks.md), [Q&A](manage-qas.md), [Locations](manage-locations.md), and [PowerApps](integrate-powerapps.md) that make content easier to find. Each of these search components includes a title, a URL, and a set of keywords that trigger it.

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
With search settings, you can tailor your content and target specific groups of users. These Microsoft Search settings control when a search result appears and who sees it:

- **Dates:** To control when content is available or unavailable, set a start date and an end date. For example, time-sensitive material appears in search result when it's relevant.
- **Country/region:** You can select countries or regions, so only users in those locations see certain content. For example, country-specific information appears in search results in those countries only.
- **Groups:** The **Groups** settings make results available only to members of selected groups. For example, if you're creating sites that pertain only to employees in the HR department, you could map this setting to the appropriate HR security group.
- **Device & OS:** Select device types or operating systems so that only users searching on those devices or using those systems will see that bookmark.
- **Targeted variations:** Use this setting to vary the content of the bookmark based on a user's device and location.

## Step 4: Test your content
After you've created Bookmarks and Q&A, it's important to verify that:
- The correct Bookmark or Q&A appears.
- All content grouped together using keywords appear together as planned.
- No unexpected results appear in search result.
- Review whether the Bookmark or Q&A has enough information.

Users and SMEs who contributed to content creation can help test and validate the search result.

## Step 5: Review and update periodically
It is important that authoritative information such as Bookmarks and Q&A are up to date. Regularly:
- Fix or remove broken or invalid URL.
- Remove Bookmarks or Q&A that are no longer relevant.
- Check for tool, site name, or team name changes.
- Consider whether the Bookmark or Q&A is authoritative enough or needs a clearer description.

## Bookmarks
You can create a bookmark in just a few steps. Each bookmark includes a title, a URL, and a set of keywords that trigger it. A bookmark can have several keywords and several bookmarks can share the same keyword, but reserved keyword can't be shared. When a Bookmark is created or modified, the search index is refreshed immediately, and the bookmark is available to users immediately.

If your organization has Promoted Results set up in SharePoint, you can import the Promoted Results into Microsoft Search and make the imported content available to your users. This is an easy way to quickly populate search results as soon as you set up Microsoft Search and make it more effective for your users. We recommend that you use promoted results from SharePoint as a reference to understand how to name and create relevant search results. 

### Add or edit a single bookmark
1. Go to **Microsoft 365 admin center**.
1. In the navigation pane, go to **Settings**, and then select **Microsoft Search**.
By default, the **Bookmarks** tab is selected.
1. To add a bookmark, select **Add new**. 
To edit a bookmark, select the bookmark in the relevant bookmark list. 
1. As you add or edit the information, the preview automatically updates.
1. Save your changes.

### Add or edit bookmark using browser extensions
Search administrators can create search content easily by using browser extensions. Install the browser extension and then go to the site you want to add as bookmark and add the site as bookmark.

Currently, browser extensions are available for Edge and Chrome. 
- To download Edge extension, go to [Microsoft Store](https://www.microsoft.com/p/microsoft-search-content-creator/9nrqdbcbwq55?activetab=pivot:overviewtab) and download the app.
- To download Chrome extension, go to [Chrome web store](https://chrome.google.com/webstore/detail/microsoft-search-content/nocnablpaoeecfmfnjoheefkogmleipm) and download the app.

### Bulk add or edit bookmarks
Search administrator can use the Import or Export features to bulk create or edit bookmarks. This is a very useful feature when an administrator wants to add or edit a large number of bookmarks. 

Use the import/export feature to:
- Bulk add bookmarks - Add details in the bookmark template file, and then import it.
- Bulk edit bookmarks - Export bookmarks to a .csv file, then edit the bookmark details in the exported .csv file, and then import the updated .csv file.
- Import promoted sites from SharePoint.
- Backup bookmarks - Export bookmarks to a .csv file.

To import or export bookmarks:
1. In the upper-right corner of **Bookmarks** tab, select **Import**. 
Select **Export** to download all the existing bookmarks in a .csv file.
1. In the right pane, choose the option to import using a .csv file or from SharePoint.
Download the template file for a list of the required fields and details. 
1. Add or edit bookmark details in the template file, and then save it on your computer. 
1. In the **Import bookmarks** pane, select **Browse** and then the .csv file that you want to import.
1. Select **Import**.

Here are some important points to be noted regarding the template file:
- Never edit data in these fields: *Id*, *Last Modified*, and *Last Modified By*
- If you include the *Id* of an existing bookmark, it will be replaced with the information in the import file.
- If there is an existing bookmark with the same title or URL, the bookmark will be updated with information in the import file.
- Not all fields in the template file are required and required fields vary depending on the bookmark state.
- Based on the *State* field, bookmarks will be saved as draft, suggested, scheduled, or they will be published automatically.
- For partners who manage multiple organizations, you can export your bookmarks from one org and import them into another. But you must remove the data in the *Id* column before you import.

#### Prevent import errors

You'll get an error if any required data is missing or invalid, and a log file is generated with more information about the rows and columns to be corrected. Make necessary edits and try importing the file again. You cannot import or save any bookmarks until all errors are resolved.

To prevent errors, make sure your import file is properly formatted and:
- Includes the header row and all the columns that were in the import template
- The column order is the same as the import template
- All columns have values, except the three that can be empty: *Id*, *Last Modified*, and *Last Modified By* 
- The *State* column is not empty, as this information is required

### PowerApps

Help your users complete tasks, such as entering vacation time or reporting expenses, by adding existing PowerApps to your bookmarks. 

#### What are PowerApps?

PowerApps is a service that lets you build business apps that run in a browser or on a phone or tablet with no coding experience required. PowerApps work in any browser and on any device and take less than a minute to add. For more on PowerApps, see:
- [Guided Learning](https://docs.microsoft.com/learn/browse/?products=powerapps)
- [Documentation](https://docs.microsoft.com/powerapps/maker/canvas-apps/get-sessionid)
- [PowerApps Home](https://make.preview.powerapps.com/environments/839eace6-59ab-4243-97ec-a5b8fcc104e4/home)

#### Add a PowerApp to a bookmark

1. Find the [App ID for the PowerApp](https://docs.microsoft.com/powerapps/maker/canvas-apps/get-sessionid#get-an-app-id) that you want to add.
1. Sign in and go to **Microsoft 365 admin center**.
1. In the navigation pane, go to **Settings**, and then select **Microsoft Search**.
1. Add a bookmark or find an existing bookmark that you want to add a **PowerApp** to.
1. In **Bookmark settings**, select **Power App**, and then **Add a Power App**.
1. Enter or paste the **App ID**.
    The height and width are automatically adjusted. Bookmarks can support both portrait and landscape orientations, but currently the size can't be changed. The bookmark preview shows a fully functional PowerApp to make it easy to test.
1. Select **Publish** or **Save to Draft**.

## Q&A

Creating a Q&A is similar to creating bookmarks. Q&A allows you to answer the user's question instead of just providing a link to webpage. You can format the answer in rich text using the available tools. If a Bookmark and a Q&A share the same keyword, the Bookmark result is shown first. Like Bookmarks, the Q&A index is refreshed immediately after a Q&A is added or changed. 

### Add or edit a single Q&A

1. Go to **Microsoft 365 admin center**.
1. In the navigation pane, go to **Settings** and select **Microsoft Search**.
1. Select **Q&A** tab. By default, the first tab (**Bookmarks**) is selected.
1. To add a Q&A, select **Add new**.
To edit a Q&A, select the Q&A in the relevant Q&A list.
1. As you add or edit the information, the preview automatically updates.
1. Save your changes.

#### Supported HTML tags

You can use HTML content or add HTML tags to your answer (description). We support these HTML tags:
 
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

Unsupported tags will either be ignored or displayed as text. Make sure you preview your cards.

### Bulk add or edit Q&A

Administrators can use the Import and Export features to bulk create or edit Q&A. This is a useful feature when administrators need to add or edit a large number of Q&A. 

Use the import and export features to:

- Bulk add Q&A items- Add details in the Q&A template file, and then import it.
- Bulk edit Q&A items - Export Q&A to a .csv file, then edit the Q&A details in the exported .csv file, and then import the .csv file.
- Backup Q&A items - Export Q&A to a .csv file.

To import or export Q&A:

1. In the upper-right corner of the Q&A tab, select **Import**. 
Select **Export** to download all the existing Q&A in a .csv file.
1. In the right pane, choose the option to import using a .csv file.
Download the template file for a list of the required fields and details. 
1. Add or edit Q&A details in the template file and save it on your computer. 
1. In the **Import Q&A** pane, select **Browse**, and then the .csv file that you want to import.
1. Select **Import**.

Here are some important points regarding the template file:

- Never edit data in these fields: *Id*, *Last Modified*, and *Last Modified By*
- If you include the *Id* of an existing bookmark, it will be replaced with the information in the import file.
- If there is an existing bookmark with the same title or URL, the bookmark will be updated with information in the import file.
- Not all fields in the template file are required and required fields vary depending on the bookmark state.
- Based on the State field, bookmarks will be saved as draft, suggested, scheduled, or they will be published automatically.
- For partners who manage multiple organizations, you can export your bookmarks from one org and import them into another. But you must remove the data in the *Id* column before you import.

**Note:** You cannot import Q&A items if there are any errors in the template file. To prevent errors, make sure your import file is properly formatted and include all the required information. 

For more information on how to prevent error, see [Prevent import errors](#prevent-import-errors).

## Locations

Locations helps your users find addresses and locate your organization's buildings by providing an accurate location for offices, campuses, and buildings, along with directions and navigation. Administrators should add all important locations of your organization. Unlike Bookmarks and Q&A, the index is not refreshed immediately, and it can take several hours for new or changed locations to appear in search results.

### Add or edit a single location

1. Go to **Microsoft 365 admin center**.
1. In the navigation pane, go to **Settings** and select **Microsoft Search**.
1. Select **Locations** tab. By default, the **Bookmarks** tab is selected on the **Microsoft Search** page.
1. To add a new location, select **Add new**.
1. To edit a location, select the location in the relevant locations list.
1. As you add or edit the information, the preview automatically updates.
1. Save your changes.

### Bulk add or edit locations

Administrators can use the Import or Export feature to bulk add or edit locations. 

Use the import/export feature to:

- Bulk add location - Add details in the location template file, and then import it. 
- Bulk edit locations - Export locations to a .csv file, then edit the location details in the exported .csv file, and then import the updated .csv file.
- Backups Locations – Export existing locations to a .csv file.

To export or import locations:

1. In the upper-right corner of the **Locations** tab, select **Import**.
Select **Export** to download the existing locations in a .csv file.
1. In the right pane, choose the option to import using a .csv file. 
Download ehe template file for a list of the required fields and details.
1. Add or edit location details in the template file, and then save it on your computer. 
1. In the **Import** locations pane, select **Browse**, and then the .csv file that you want to import.
1. Select **Import**.

Here are some important points regarding the template file:

- Never edit data in these fields: *Id*, *Last Modified*, and *Last Modified By*
- If you include the *Id* of an existing bookmark, it will be replaced with the information in the import file.
- If there is an existing bookmark with the same title or URL, the bookmark will be updated with information in the import file.
- Not all fields in the template file are required and required fields vary depending on the bookmark state.
- Based on the *State* field, bookmarks will be saved as draft, suggested, scheduled, or they will be published automatically.
- For partners who manage multiple organizations, you can export your bookmarks from one org and import them into another. But you must remove the data in the *Id* column before you import.

**Note:** You cannot import Locations if there are any errors in the template file. To prevent errors, make sure your import file is properly formatted and include all the required information. 

For more information on how to prevent error, see [Prevent import errors.](#prevent-import-errors)

## Review and update Bookmarks, Q&A, and Locations

 Microsoft Search provides usage statistics for Bookmarks, Q&A, and Locations. The usage statistics shows how users are engaging with your search results and whether users are finding what they are looking for, or are there any gaps in the available content? It helps administrator monitor performance and take appropriate actions to fine tune the search results. 

### Get details about Bookmarks, Q&A and Locations

See how many Bookmarks, Q&A, and Locations have been published, scheduled, or suggested. Use the dashboard to see Bookmark, Q&A, or Location totals by status:

- **Published:** The number of published results that are available to users.
- **Scheduled:** The number of scheduled results in the publish pipeline.
- **Suggested:** The number of suggestions from users.

Suggested Bookmarks, Q&A, and Locations are a good indicator of gaps in your content. It will help you understand what your users are looking for, and not finding. This could indicate that you need to create more Bookmarks, Q&A, or Locations or you need to update your existing content by using better keywords, reserved keywords, and search strings to improve the discoverability of content.

### Review top search queries

Find out which searches have generated the most impressions over the last 90 days. Impression refers to how many times a page was viewed in search result. The **Top Queries** card shows the top 25 user searches for each result type with the total number of searches and their click-through rate (CTR). Use this report to identify search query volume and to determine queries with high and low search activity. 

Low search count may indicate user dissatisfaction either because users are not looking for those search content or are using different keywords to find that content. CTR shows how often users select the promoted results and how useful your query rules and results are to users. A low CTR indicates that users are finding the content but are making the determination that the content does not meet their search. In such cases, administrators may decide to review the content and ensure that it corresponds with the user’s search and update titles, descriptions, and keywords to align them with the user search queries. 

### Analyze impressions by result type

Easy-to-read graphs in the **Impression Distribution by Result Type** card show impressions over various time frames. The timeline shows the daily number of impressions for a result type. Determine which result type is most frequently, or infrequently, used. Infrequent use of particular result type does not necessarily mean that the result types are not good. It just shows how users are using the search result.

Use this report to understand what result types users are using and any changes in user behavior over a period of time. If a particular result type is preferred by users, administrators may decide to create more search results of the same types or  to review the keywords of results types not used by users to ensure that keywords are appropriate.
