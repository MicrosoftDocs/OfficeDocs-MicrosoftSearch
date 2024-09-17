---
ms.date: 10/02/2019
title: "Searching and validating indexed content Microsoft Graph connectors"
ms.author: danielabo
author: danielabom
audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
description: "Learn how to search and validate whether some content is indexed in Microsoft Search and Microsoft 365 Copilot."
---

# Searching and validating indexed content Microsoft Graph connectors

You can use the index browser **to test indexing** when you cannot find a particular item during connection testing. If you need **to verify properties and user access**, it helps **review the metadata and access control lists (ACLs)** of indexed items. Additionally, it is beneficial for **troubleshooting search issues**; if users report problems accessing items, this feature confirms whether the item was indexed correctly and includes the correct data.

:::image type="content" source="media/manage-connector/index-search.png" alt-text="Screenshot that shows connector what users can see when they enter an item ID of an indexed item.":::

## About the index browser

When you enter an item ID to check its index status, you can view the following details if the item is indexed.

- Name of the Content - The name of the indexed item.
- Status - The current status of the item and its last refresh time.
- Properties - Indicates the status of all properties defined during configuration for the item.
- Permissions -  Lists all groups and individual users associated with the item. If the status is **allow**, all users in those groups can view the item. If the status is **deny**, users in those groups cannot access the item. If access permissions are configured as **Allow everyone** instead of **Only people with access** for the connection, all items in the index are visible to everyone, and no specific permissions are enforced.
- Check user access - Allows searching for a specific user to verify their access to the item. Enter the user name or email address to display a list of groups to which the user belongs. If the user is denied access to any of these groups, their overall permission to view the item is revoked.

>[!NOTE]
>- In permissions, you can see users shown individually (outside of a group) in the data source and groups within the data source. To check for a user present in a group, use **Check user access**. 
>- If a user doesn't appear in **Check user access**, it may be due to a failed user mapping or the user not being discovered (e.g., the AAD user ID was not found). To resolve this, check if the user has access in the data source, review the user mapping formula, and the error reports.

To search for indexed content, enter the unique identifier of the item in the index browser. 

|Connector name|Input per item ID|Where to find the item ID|
|:------------ |:------------ |:------------|
|ADO WI|ID|The ID is the work item ID.|	
|ADO Wiki|OrganizationName, page ID|It can be found in the URL e.g- https://dev.azure.com/O365Exchange/Demolink/_wiki/O365%20Core.wiki/244161/xyzItemId: O365Exchange/244161|		
|ServiceNow KB|Sys_Id.DisplayValue|Navigate to the record where you are looking for a sys_id, right-click the header bar, and select Copy sys_id.You can also click the Hamburger > Copy sys_id. For more information: https://docs.servicenow.com/csh?topicname=c_UniqueRecordIdentifier.html&version=latest|
|ServiceNow Catalog|Sys_Id.value|Navigate to the record where you are looking for a sys_id, right-click the header bar, and select Copy sys_id.You can also click the Hamburger > Copy sys_id. For more information: https://docs.servicenow.com/csh?topicname=c_UniqueRecordIdentifier.html&version=latest| 		
|ServiceNow Tickets|Sys_Id.value|Navigate to the record where you are looking for a sys_id, right-click the header bar, and select Copy sys_id.You can also click the Hamburger > Copy sys_id. For more information: https://docs.servicenow.com/csh?topicname=c_UniqueRecordIdentifier.html&version=latest|		
|Salesforce|ID|It can be found in the URL e.g- - https://democompany123-dev-ed.my.salesforce.com/00T5w00008iy76x -Item ID: 00T5w00008iy76x|
|Intranet (Cloud/OnPrem)|URL|Final Url in lowercase|Jira issue ID	Follow the link : https://confluence.atlassian.com/jirakb/how-to-get-issue-id-from-the-jira-user-interface-1115156394.html#:~:text=User%20needs%20to%20get%20the%20issue%20id%20in%20an%20easier|
|Confluence (Cloud/OnPrem)|page blog post ID|It can be found in the item ID of the URL http://confluencedatacenter.dummy.dummyapp.azoro.com:1234/pages/viewinfo.action?pageId=13795332 itemID: 13795332. Example in the Confluence Cloud: URL from the data source - 	https://dummy_URL.atlassian.net/wiki/spaces/xyz/pages/5242881 page ID - 5242881| 	
|CSV|Unique identifier list, item key|Admin configured details.|
|Azure SQL, Oracle DB, MS SQL|Values to all the columns in unique key columns|Admin configured details.|
|Mediawiki|page ID, namespace, sourceUrl|Admin configured details.| 	 	
|ADLS gen 2|File URI|Admin configured details.| 	 	
|Sharepoint|GUID|Admin configured details.| 	 	
|FileShare|filepath|Admin configured details.|  	 	
|Custom connector|item ID|Admin configured details.|  
|SAP|user ID|Admin configured details.|  	 	

## Examples
### Example 1: The item status is partially indexed

It indicates that the item is missing some information, such as properties, user details, or content, but remains searchable in Microsoft Search and Microsoft 365 Copilot. To ensure the item is complete, review the Errors tab for details.

### Example 2: The item status is deny all

It indicates that the item is indexed but remains inaccessible to all users, as shown by an empty response in the permissions tab. Although the item is present in the index, users can't view it.

In the case of a ServiceNow connector, the **Deny all** status may result from different causes

- Advanced criteria on an item - If advanced criteria are applied to an item in the deny list, it may be marked as **Deny all.** To resolve it, try removing the advanced criteria and triggering a full crawl. For more information, see the troubleshooting section of each connector. 

- Advanced criteria on a knowledge base - If advanced criteria on a knowledge base deny list affect all articles within that knowledge base. It can result in a **Deny all** status for those articles. Identify the knowledge base the item belongs to and remove the advanced criteria. For more information, see the troubleshooting section of each connector. 

Additionally, temporary issues may cause a **Deny all** status, which could be resolved during the next full crawl.

### Example 3: The item status is allowed for everyone

When an item is configured to be visible to everyone, it is accessible to all users within the organization, regardless of the permissions set in the data source.

If an item is discovered but not indexed, check the Errors tab for any issues that prevented the indexing process.

>[!NOTE]
>- Changes to user or group permissions (ACL) may take up to 24 hours to reflect in Microsoft Search and Microsoft 365 Copilot.
>- Permissions updates occur during a full crawl, not an incremental crawl.
>- If your data source permissions change after the last full crawl, a new full crawl must be triggered on-demand or scheduled to update the index.
>- When testing in Microsoft Search or Microsoft 365 Copilot, make sure that you are searching with a searchable or queryable property. For more information, see (/microsoftsearch/manage-search-schema). 

