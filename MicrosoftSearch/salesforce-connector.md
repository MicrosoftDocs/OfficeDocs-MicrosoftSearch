---
title: "Salesforce connector for Microsoft Search"
ms.author: rusamai
author: rsamai
manager: jameslao
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150

ROBOTS: NOINDEX, NOFOLLOW


description: "Set up the Salesforce connector for Microsoft Search"
---
# Salesforce connector

With the Salesforce Graph connector, your organization can index Contacts, Opportunities, Leads and Accounts objects in your Salesforce instance. After you configure the connector and index content from Salesforce, end users can search for those items from any Microsoft Search client

This article is for [Microsoft 365](https://www.microsoft.com/microsoft-365) administrators or anyone who configures, runs, and monitors a Salesforce connector. It explains how to configure your connector and connector capabilities, limitations, and troubleshooting techniques.

>[!IMPORTANT] 
> The Salesforce Graph connector currently supports Summer ’20, Spring’20, Winter’20, and Summer ’19 versions. 

<br>

## Connection settings


<br>
To connect to your Salesforce instance, you need your Salesforce instance URL, the Client ID, and Client Secret for OAuth authentication. The following steps explain how you or your Salesforce administrator can get this information from your Salesforce account: 

- Log in to your Salesforce instance and go to Setup 

- Navigate to Apps -> App Manager. 

- Click on **New connected app**. 

- Complete the API section as follows: 

    - Select the checkbox for **Enable Oauth Settings**.

    - Specify the Callback URL as: *https://gcs.office.com/v1.0/admin/oauth/callback* 

    - Select these required Oauth scopes. 

        - Access and manage your data (api) 

        - Perform requests on your behalf at any time (refresh_token, offline_access) 

    - Select the checkbox for **Require secret** for web server flow. 

    - Save the app. 
    
![API Enable OAuth Settings asking for callback URL, selected OAuth Scopes, and a checkbox for require secret for web server flow](media/sf1.png)

-	Copy the consumer key and the consumer secret. These will be used as the Client ID and the Client Secret when you configure the Connection Settings for your Graph Connector in the Microsoft 365 admin portal.

![Select the ](media/sf2.jpg)
- Perform the following steps in your Salesforce instance to ensure that refresh tokens do not expire: 
	- Go to Apps -> App Manager
	- Find the app you just created and select the drop down on the right. Click **Manage**
	- Click **edit policies**
	- For refresh token policy, select **Refresh token is valid until revoked**

![Select the Refresh Token Policy named "Refresh token is valid until revoked "](media/sf3.jpg)

You can now return to the Connection settings page  scan now go to the back to the connector settings screen in the M365 admin center. 
	- For the Instance URL, use https://[domain].my.salesforce.com where domain would be your Salesforce domain for your organization. 
	- Enter the Client ID and Client Secret you got from the previous steps and click Sign in. 
The first time you do this, you will get a pop up asking you to login to Salesforce with your admin username and password. 

![Login pop up asking for Username and password](media/sf4.png)

Enter your credentials and hit Log in. The screenshot below shows a successful login.

![The successful login is indicatd by a green banner that says "Connection successful". This banner is located under the Instance URL](media/sf5.png)

>[!NOTE] If your organization uses single sign-on (SSO), you can click on **Use Custom Domain** to enter the domain and click **Continue**. It will go to your organization specific login page where you will have an option to login with SSO. If you do not see the pop up, it might be getting blocked in your browser and you must allow pop-ups and redirects.*

## Manage search permissions
You will need to select the users that will see search results from this data source. If you choose to create an Access Control List (ACL) that allows only certain Azure Active Directory (AAD) or Non-AAD users to see the search results, you will then need to map the identities. 

### Select Permissions
You can choose to allow everyone in your organization to see search results from this Connector or create an Access Control List (ACL) that allows only certain users to see search results from this Salesforce Connector. ACL’s can include Azure Active Directory (AAD)identities, Non-AAD identities, or both.Learn more about the identities in the [Map your non-Azure AD Identities](user-mapping.md) page.

![Select permissions.Either "Only people with access to this data source" or "Everyone""](media/sf6.png)

### Map non-AAD identities 
If you created an Access Control List that includes non-AAD identities, you will be asked to select the AAD user property that will be used to manage search permissions. The drop-down menu of options includes Active Directory SID, User Principal Name, and AAD ID. 

Once you select the AAD user property, select at least one non-AAD property to map to it, then enter a regular expression (regex) to apply to the non-AAP property. The drop-down menu of identity property options includes Name, Alias, Email, First Name, Last Name, Federation Identifier, and User Name. Repeat this step for as many non-AAD properties as you want to map to the AAD property you selected.

Finally, create a formula that combines the regex outputs from the non-Azure AAD properties you selected with the AAD property you selected, and enter the formula in the space provided.

### Map AAD identities
If you created an Access Control List that includes AAD identities, you will be asked to... select how your organization currently maps AAD properties with the federation ID in Salesforce. The available properties are listed in a drop-down menu that includes the following options: FirstName, LastName, Domain, User Principal Name, Active Directory SID, AAD ID and Domain. 
 
The screenshot below shows an example of a completed mapping. To map with that field, selects that property from the dropdown, add a formula to complete the mapping to the federation ID and then click on Preview to see the validation happen with some sample users. 

![Form an expression by selecting the Azure AD user property and add a format for your expression.](media/sf7.png)

## Assign property labels 
You can assign source properties to property labels. By default, some of the Labels like ”Title”, “url”, and  “LastModifiedBy” have already been assigned source properties. While this step is not mandatory, having some property labels will improve the search relevance and ensure more accurate search results for end users.

![Assign your source properties to property labels.](media/sf8.png) 


## Manage Schema
You can select what source properties should be indexed so that they can show up in search results. The connection wizard by defaults selects a search schema based on a set of source properties. You can modify it by selecting the check boxes for each property and attribute in the search schema page. Search schema attributes include Search, Query, Retrieve and Refine. 
Refine allows you to define the properties which can be later used as custom refiners or filters in the search experience.  
![Select the schema for each source property. The options are Query, Search, Retrieve, and Refine](media/sf9.png)

## Set the refresh schedule

The Salesforce connector only supports refresh schedules for full crawls currently.

>[!Important] A full crawl finds deleted objects and users that were previously synced to the Microsoft Search index. 

The recommended schedule is one week for a full crawl.

## Known Limitations

- The connector does not currently support Apex based , territory-based sharing and sharing using personal groups from Salesforce.
- There is a known bug in the Salesforce API that the Graph Cconnector uses where the private org wide defaults for leads is not honored currently.  
- If a field has field level security (FLS) set for a profile, the Graph Cconnector will not ingest that field for any profiles in that Salesforce org. Users will thus not be able to search on values for those fields, nor will it  show up in the results.  
- **Any FLS set up will be honored during the Full syncs of the connector.** 
- In the Manage Schema screen these common standard property names are listed once and the selection done to make them queryable, searchable and retrievable apply to all or none. 
    - Name
    - Url 
    - Description
    - Fax
    - Phone
    - MobilePhone
    - Email
    - Type
    - Title
    - AccountId
    - AccountName
    - AccountUrl
    - AccountOwner
    - AccountOwnerUrl
    - Owner
    - OwnerUrl
    - CreatedBy 
    - CreatedByUrl 
    - LastModifiedBy 
    - LastModifiedByUrl 
    - LastModifiedDate
    - ObjectName 


