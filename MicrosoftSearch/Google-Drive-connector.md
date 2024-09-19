--- 

title: "Google Drive Graph connector for Microsoft Search and Copilot" 
ms.author: anggao
author: ms-anggao
manager: jecui
audience: Admin
ms.audience: Admin 
ms.topic: article 
ms.service: mssearch 
ms.localizationpriority: Medium 
search.appverid: 
- BFB160 
- MET150 
- MOE150 
description: "Set up the Google Drive Graph connector for Microsoft Search and Copilot" 
ms.date: 09/19/2024
---

# Google Drive Graph connector (Preview)

With the Microsoft Graph connector, your organization in M365 can index files that accesslble to anyone in Google Drive, using in Microsoft Copilot and Search. 

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors Google Drive connector. 

>[!NOTE]
>The Google Drive connector is in preview. If you wish to get early access to try it, sign up using [this form](https://forms.office.com/r/JniPmK5bzm).

## Capabilities
- Access Google Drive files using the power of Semantic search
- Retain ACLs defined by your organization (coming soon) 
- Customize your crawl frequency
- Create workflows using this connection and plugins from Microsoft Copilot Studio


## Limitations
- Folder, replies & comments aren't inxedbale 
- Doesn't crawl user identities and access permissions.
- Only files accessible to anyone in Google Drive are indexed.
- All files indexed using the Google Drive connector are visible to all Microsoft 365 users in your tenant, from Microsoft Search or Copilot.

## Prerequisites
Before you create a Google Drive connector, you must:
### 1. Be a Google Workspace super admin role or be granted the access
Either be granted access by a super admin role or are a user with administrative privileges. You do not need a super admin role for yourself if you have been granted access by a super admin role.

### 2. Configure Google Drive Service Account connection credentials
Configured Google Drive Service Account connection credentials containing your admin account email, client email (service account email), and private key. See [Create and delete service account keys](https://cloud.google.com/iam/docs/keys-create-delete) for more info.

### 3. Create a Google Cloud Service Account
Create a Google Cloud Service Account (an account with delegated authority to assume a user identity) with Enable G Suite Domain-wide Delegation activated for server-to-server authentication, and then generate a JSON private key using the account. See [Create service accounts](https://cloud.google.com/iam/docs/service-accounts-create) for more info.

### 4. Add required APIs in your user account
Add Admin SDK API and Google Drive API in your user account.

### 5. Add the OAuth scopes to your service account
Add (or ask a user with a super admin role to add) the following OAuth scopes to your service account using a super admin role. These API scopes are needed to crawl all documents, and access control (ACL) information for all users in a Google Workspace domain:

`https://www.googleapis.com/auth/admin.directory.user.readonly`


`https://www.googleapis.com/auth/drive.readonly`   


## Set up

### 1. Display name   
A display name is used to identify each reference in Copilot, helping users easily recognize the associated file or item.   Display name also signifies trusted content.

### 2. Google Apps domain
To sign up for Google Workspace, you need an internet domain name, like your-company.com. This domain can host a website (`www.your-company.com`) and email (`info@your-company.com`). See [What is a domain?](https://support.google.com/a/answer/177483?hl=en&ref_topic=3540977&sjid=7603839478714180429-AP) for more info.

### 3. Google Apps administrator account email
Enter the email of a Google Apps administrator account in the `user@company.com` format.

### 4. Private key file
Copy and paste the content of private key file that you created when you authorized your Microsoft organization to access your users' Google Drive.  

### 5. Rollout to limited audience
Deploy this connection to a limited user base if you want to validate it in Copilot and other search surfaces before expanding the rollout to a broader audience.

For other settings, like Access Permissions, Data inclusion rules, Schema, Crawl frequency etc., we set defaults based on what works best with data in Google Drive. The default values settings are as follows.

**Page** | **Settings** | **Default Values**
--- | ---- | ---
Users | Access Permissions | All files that are accessible to anyone in Google Drive are visible to all Microsoft 365 users in your tenant, from Microsoft Search or Copilot.
Content | Index Content | All published posts and pages are selected by default.
Content | Manage Properties | To check default properties and their schema, [click here](#content).
Sync | Incremental Crawl | Frequency: Every 15 mins
Sync | Full crawl | Frequency: Every day

If you want to edit any of these values, you need to choose the **Custom Setup** option. 

## Custom Setup 

Custom setup is for those admins who want to edit the default values for settings. Once you click on the ‘Custom Setup’ option, you should see three other tabs – Users, Content, and Sync. 

### Users 

**Access permissions**

Currently only files that are accessible to anyone in Google Drive are indexed and visible to all Microsoft 365 users in your tenant, from Microsoft Search or Copilot.

### Content 

**Manage Properties**

Here, you can add or remove available properties from your Google Drive data source. Assign a schema to the property (define whether a property is **searchable, queryable, retrievable or refinable**), change the semantic label and add an alias to the property. Properties that are selected by default are:

**Source Property** | **Label** |**Description**| **Schema**
--- | ---- | --- | ---
CreatedTime | Created date time | The time at which the file was created.  | Search, Query, Retrieve
Description |  | A short description of the file.  | 
FileExtension | File extension | The final component of fullFileExtension. This parameter is only available for files with binary content in Google Drive.  | Query, Refine, Retrieve
FileType |  | The type of the file.  | 
IconLink | IconUrl | A static, unauthenticated link to the file's icon.  | Retrieve
LastModifingUser | Last modified by | The last user to modify the file. This field is only populated when the last modification was performed by a signed-in user.  | Query, Retrieve, Search
Link | url | A link for opening the file in a relevant Google editor or viewer in a browser.  | Retrieve
Name | Title | The name of the file.  | Query, Retrieve, Search
Owner | Created by | The owner of this file. Only certain legacy files may have more than one owner. This field isn't populated for items in shared drives.  | Search, Query, Retrieve
ParentFolderLink |  |  A link for the parent folder containing the file.  | Retrieve
ParentFolderName |  | The name of the parent folder containing the file.  | Search, Query, Retrieve
Size |  | Size in bytes of blobs and first party editor files.  | Search, Query, Retrieve


### Sync 

You can configure full and incremental crawls based on the scheduling options present here. By default, incremental crawl is set for every 15 minutes, and full crawl is set for every day. If needed, you can adjust these schedules to fit your data refresh needs.

## Troubleshooting
### Invalid credentials detected. Check the credential info and check the permissions of the service account.
This error occurs when the service account lacks necessary permissions for Google Drive access. Check the credentials info of the account and ensure that they are correctly filled in the setup page. 
### The required permissions for users/files are missing.
Authentication error, one or more required OAuth scopes to your service account are missing. Your service account must include both API scopes:

`https://www.googleapis.com/auth/admin.directory.user.readonly` 

`https://www.googleapis.com/auth/drive.readonly` 
### Failed to capture file information. Ensure the workspace is not empty and has files accessible to the admin.
 During the connector setup, at least one file must be present in your organization's workspace to test the connection successfully.


## What's next

After publishing your connection, you can review the status under the **Data Sources** tab in the [admin center](https://admin.microsoft.com). To learn how to make updates and deletions, see [Manage your connector](manage-connector.md).

If you have any other issues or want to provide feedback, reach out to us at [Microsoft Graph | Support](https://developer.microsoft.com/en-us/graph/support)
