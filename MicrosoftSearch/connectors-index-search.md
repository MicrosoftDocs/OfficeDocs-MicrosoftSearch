---
ms.date: 10/02/2019
title: "Searching and validating indexed content Microsoft Graph connectors"
author: danielabom
audience: Admin
ms.topic: article
ms.service: mssearch
ms.localizationpriority: medium
description: "Learn how to search and validate whether some content is indexed in Microsoft Search and Microsoft 365 Copilot."
---

# Searching and validating indexed content Microsoft Graph connectors

You can use an index browser to search and determine if specific content is indexed. If an item is indexed, you can view its associated properties, metadata, permissions, and access control lists (ACLs).

:::image type="content" source="media/manage-connector/index-search.png" alt-text="Screenshot that shows connector what users can see when they enter an item ID of an indexed item.":::

## Locate the item ID
To search for indexed content, enter the unique identifier of the item in the index browser. 

|Connector name|Input per item ID|Where to find the item ID|
|:------------ |:------------ |:------------|
|ADO WI|ID|The ID is the work item ID.|	
|ADO Wiki|OrganizationName, page ID|It can be found in the URL e.g- https://dev.azure.com/O365Exchange/Demolink/_wiki/O365%20Core.wiki/244161/xyzItemId: O365Exchange/244161.|		
|ServiceNow KB|Sys_Id.DisplayValue|Navigate to the record where you are looking for a sys_id, right-click the header bar, and select Copy sys_id.You can also click the Hamburger > Copy sys_id. For more information: https://docs.servicenow.com/csh?topicname=c_UniqueRecordIdentifier.html&version=latest|
|ServiceNow Catalog|Sys_Id.value|Navigate to the record where you are looking for a sys_id, right-click the header bar, and select Copy sys_id.You can also click the Hamburger > Copy sys_id. For more information: https://docs.servicenow.com/csh?topicname=c_UniqueRecordIdentifier.html&version=latest| 		
|ServiceNow Tickets|Sys_Id.value|Navigate to the record where you are looking for a sys_id, right-click the header bar, and select Copy sys_id.You can also click the Hamburger > Copy sys_id. For more information: https://docs.servicenow.com/csh?topicname=c_UniqueRecordIdentifier.html&version=latest| 		 		
|Salesforce|ID|It can be found in the URL e.g- - https://democompany123-dev-ed.my.salesforce.com/00T5w00008iy76x -Item ID: 00T5w00008iy76x.|
|Intranet (Cloud/OnPrem)|URL|Final Url in lowercase|Jira issue ID	Follow the link : https://confluence.atlassian.com/jirakb/how-to-get-issue-id-from-the-jira-user-interface-1115156394.html#:~:text=User%20needs%20to%20get%20the%20issue%20id%20in%20an%20easier|
|Confluence (Cloud/OnPrem)|page blog post ID|It can be found in the item ID of the URL http://confluencedatacenter.dummy.dummyapp.azoro.com:1234/pages/viewinfo.action?pageId=13795332 itemID: 13795332. Example in the Confluence Cloud: URL from the data source - 	https://dummy_URL.atlassian.net/wiki/spaces/xyz/pages/5242881 page ID - 5242881.| 	
|CSV|Unique identifier list, item key|Admin configured details.|
|Azure SQL, Oracle DB, MS SQL|Values to all the columns in unique key columns|Admin configured details.|
|Mediawiki|page ID, namespace, sourceUrl|Admin configured details.| 	 	
|ADLS gen 2|File URI|Admin configured details.| 	 	
|Sharepoint|GUID|Admin configured details.| 	 	
|FileShare|filepath|Admin configured details.|  	 	
|Custom connector|item ID|Admin configured details.|  
|SAP|user ID|Admin configured details.|  	 	

## Permissions
This tab lists the groups from the data source with permissions for the item ID. If the status is **allow**, all users in those groups can see the item. If the status is **deny**, users in those groups can't access the item.

### Check user access
To check user access, enter the user name or email address. A list of groups to which the user belongs is displayed. If the user is denied access to any of these groups, their overall permission to view the item is revoked.
