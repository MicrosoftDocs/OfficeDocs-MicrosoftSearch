---
ms.date: 10/02/2019
title: "Searching and validating indexed Content Microsoft Graph connectors"
author: danielabom
audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
description: "Learn how to search and validate whether some content is indexed in Microsoft Search and Microsoft 365 Copilot."
---

# Searching and validating indexed Content Microsoft Graph connectors

You can now search to determine if specific content is indexed. You can also review its associated properties and access permissions.

## Using this feature
To search for index content, you must enter the unique identifier for each document, content, or item.

|Connector name|Input per item ID|Where to find the item ID|
|:------------ |:------------ |:------------|
|ADO WI|ID|ID is the work item ID.|	
|ADO Wiki|OrganizationName, PageId|It can be found in the URL e.g- https://dev.azure.com/O365Exchange/Demolink/_wiki/O365%20Core.wiki/244161/xyzItemId: O365Exchange/244161.|		
|ServiceNow KB|Sys_Id.DisplayValue|Navigate to the record where you are looking for a sys_id, right-click the header bar, and select Copy sys_id.You can also click the Hamburger > Copy sys_id. For more information: https://docs.servicenow.com/csh?topicname=c_UniqueRecordIdentifier.html&version=latest|
|ServiceNow Catalog|Sys_Id.value|Navigate to the record where you are looking for a sys_id, right-click the header bar, and select Copy sys_id.You can also click the Hamburger > Copy sys_id. For more information: https://docs.servicenow.com/csh?topicname=c_UniqueRecordIdentifier.html&version=latest| 		
|ServiceNow Tickets|Sys_Id.value|Navigate to the record where you are looking for a sys_id, right-click the header bar, and select Copy sys_id.You can also click the Hamburger > Copy sys_id. For more information: https://docs.servicenow.com/csh?topicname=c_UniqueRecordIdentifier.html&version=latest| 		 		
|Salesforce|ID|It can be found in the URL e.g- - https://democompany123-dev-ed.my.salesforce.com/00T5w00008iy76x -Item ID: 00T5w00008iy76x.|
|Intranet (Cloud/OnPrem)|URL|Final Url in lowercase|Jira issue ID	Follow the link : https://confluence.atlassian.com/jirakb/how-to-get-issue-id-from-the-jira-user-interface-1115156394.html#:~:text=User%20needs%20to%20get%20the%20issue%20id%20in%20an%20easier|
|Confluence (Cloud/OnPrem)|Page/BlogPost ID|It can be found in the item ID in the URL of page information http://confluencedatacenter.dummy.dummyapp.azoro.com:1234/pages/viewinfo.action?pageId=13795332 itemID: 13795332. Example in the Confluence Cloud: URL from the data source - 	https://dummy_URL.atlassian.net/wiki/spaces/xyz/pages/5242881 page ID - 5242881.| 	
|CSV|Unique identifier list, item key|Admin configured details.|
|Azure SQL, Oracle DB, MS SQL|Values to all the columns in unique key columns|Admin configured details.|
|Mediawiki|page ID, namespace, sourceUrl|Admin configured details.| 	 	
|ADLS gen 2|File URI|Admin configured details.| 	 	
|Sharepoint|GUID|Admin configured details.| 	 	
|FileShare|filepath|Admin configured details.|  	 	
|Custom connector|item ID|Admin configured details.|  
|SAP|user ID|Admin configured details.|  	 	

### Troubleshooting search and access issues
When testing your connection and unable to locate a particular item. b. Property and User Access Verification: When an item is indexed, you need to review its associated metadata and access control lists (ACLs). c. Troubleshooting Search Issues: If users report issues accessing items, use this feature to confirm proper indexing and correct data inclusion.

About the Index Browser: When you enter an item ID to check its indexing status, if the item is indexed, you will see the following details:

*Properties: Displays the status of all properties defined during the item’s configuration.
*Permissions: Lists all groups and individual users associated with the item.
*Check user access: Allows you to search for a specific user to verify their access to the item.

The index browser shows the name of the content, its status, and the date it was last refreshed.

Image 

