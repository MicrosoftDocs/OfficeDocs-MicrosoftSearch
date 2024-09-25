--- 

title: "CSV Microsoft Graph connector for Microsoft Search and Microsoft 365 Copilot" 
ms.author: rchanda 
author: rchanda 
manager: harshkum 
audience: Admin
ms.audience: Admin 
ms.topic: article 
ms.service: mssearch 
ms.localizationpriority: medium 
search.appverid: 
- BFB160 
- MET150 
- MOE150 
description: "Set up the CSV Microsoft Graph connector for SharePoint or Azure Data Lake Storage sources." 
ms.date: 03/08/2022
---

# CSV Microsoft Graph connector

The CSV Microsoft Graph connector allows your organization to ingest content from CSV files stored in SharePoint libraries and Azure Data Lake Storage (ADLS). After you configure the connector and index content from these sources, end users can find CSV files in Microsoft Search and Microsoft 365 Copilot.

This article is for anyone who configures, runs, and monitors a CSV Microsoft Graph connector. It supplements the general setup process and shows instructions that apply only to this connector.

<!---## Before you get started-->
## Before you get started

- Make sure there's no whitespace in the CSV headers

- For a SharePoint data source, you can authenticate using either of the two OAuth providers: **Microsoft Entra ID** (recommended) or **SharePoint provider** ([retiring soon](/sharepoint/dev/sp-add-ins/retirement-announcement-for-azure-acs)).
    - For authenticating using Microsoft Entra ID you'll need to create and register an app on Microsoft Entra ID.
    - For authenticating using SharePoint provider you'll need to create a SharePoint app with OAuth configuration.

- For an ADLS data source, you'll need to create an ADLS storage account.

## SharePoint data source

### Upload your CSV files

Verify the .csv files you want to index have been uploaded to a SharePoint document library. You can use an existing SharePoint site or create a new one.

### Create an app on Microsoft Entra ID

1. Go to the [Azure portal](https://portal.azure.com) and sign in with admin credentials for the tenant.

2. Navigate to **Microsoft Entra ID** -> **Manage** -> **App registrations** from the navigation pane and select **New registration**.

3. Provide a name for the app and select **Register**.

4. Make a note of the application (client) ID.

5. Open **API permissions** from the navigation pane and select **Add a permission**.

6. Select **SharePoint** and then **Delegated permissions**.

7. Search for the following permissions and select **Add permissions**. <br>
    a. AllSites.Read<br>
    b. User.Read.All

8. Select **Grant admin consent for [TenantName]** and confirm by selecting **Yes**.

9. Check that the permissions are in the "**granted**" state.

10. Open **Authentication** from the navigation pane and add the following under Redirect URIs (Authorization callback URIs):
    - For **M365 Enterprise**: `https://gcs.office.com/v1.0/admin/oauth/callback](https://gcs.office.com/v1.0/admin/oauth/callback`
    - For **M365 Government**: `https://gcsgcc.office.com/v1.0/admin/oauth/callback](https://gcsgcc.office.com/v1.0/admin/oauth/callback`

#### Configuring the client secret for authentication

1. Go to the [Azure portal](https://portal.azure.com) and sign in with admin credentials for the tenant.

2. Open **App Registration** from the navigation pane and go to the appropriate App. Under **Manage**, select **Certificates and Secrets**.

3. Select **New Client Secret** and select an expiry period for the secret. Copy the generated secret and save it because it is not shown again.

4. Use this Client secret and the application ID to configure the connector.

### Create a SharePoint app with OAuth configuration

1. Go to  `https://Org-Name.sharepoint.com/sites/mysite/_layouts/15/appregnew.aspx`.
2. On the Client ID and Client Secret fields, select **Generate**.
3. For Title, enter an app name.
4. In the App Domain field, enter `www.gcs.com`.
5. In the Redirect URL field, enter `https://www.gcs.com`.
6. Select **Create**.
7. Copy the app configuration information, including the Client ID and Client Secret. You'll need it when you set up the CSV connector.

#### Enable app permissions to allow customAppAuthentication

In PowerShell ([SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)), run these commands in administrative mode. Use the email address of the admin configuring the connector and your organization name. When the password pop-up appears, the admin should enter their password.

```powershell
Install-Module -Name Microsoft.Online.SharePoint.PowerShell
$adminUPN=”<admin@contoso.onmicrosoft.com>”
$orgName=“<contoso>”
$userCredential = Get-Credential -UserName $adminUPN -Message "Enter your password."
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $userCredential
Set-spotenant –DisableCustomAppAuthentication $false
```

> [!NOTE]
> If you're using PowerShell 7, use this command first `Import-Module microsoft.online.sharepoint.powershell -UseWindowsPowerShell`

> [!NOTE]
> If you're using multifactor authentication, use `Connect-SPOService -Url https://$orgName-admin.sharepoint.com`.

#### Complete the app configuration

1. Go to `https://Org-Name.sharepoint.com/sites/mysite/_layouts/15/appinv.aspx`.
2. In the App ID field, paste the client ID of the SharePoint app and select **Lookup**.
3. In the permission Request XML field, paste this code and select **Create**.

```xml
<AppPermissionRequests AllowAppOnlyPolicy="true">
    <AppPermissionRequest Scope="http://sharepoint/content/sitecollection/web" Right="Read" />
</AppPermissionRequests>
```

4. Select **Trust it**.

## ADLS data source

### Create an ADLS storage account

For step-by-step guidance, see [Create a storage account](/azure/storage/common/storage-account-create#create-a-storage-account-1). To allow file storage capabilities, on the Advanced tab, select **Enable hierarchical namespace** and **Create a container for this site**.

When you set up the CSV Microsoft Graph connector, you'll need to provide a primary storage connection string. To find it, open the storage account you created and select **Access keys**. Select **Show keys** and copy the connection string for Key1.

## Step 1: Add a Microsoft Graph connector in the Microsoft 365 admin center

[Add CSV Microsoft Graph connector](https://admin.microsoft.com/adminportal/home#/MicrosoftSearch/Connectors/add?ms_search_referrer=MicrosoftSearchDocs_CSV&type=CSV)

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup 
instructions.-->

## Step 2: Name the connection

Follow the general [setup instructions](./configure-connector.md).
<!---If the above phrase does not apply, delete it and insert specific details for your data source that are different from general setup 
instructions.-->

## Step 3: Configure connection settings

The data source settings are different for SharePoint and ADLS.

> [!NOTE]
> Ensure that your csv file does not have any formatting or spaces (‘ ‘) present in header rows.

### For a SharePoint source

1. In the Data Source settings, select **SharePoint** as your datasource.
2. In **SharePoint site**, enter the site URL, `https://Org-Name.sharepoint.com/Site-Name`, for example.
3. In **Document Library**, enter the name of the library where the .csv files are stored.
4. In **OAuth provider**, you can either select **SharePoint Provider (retiring soon)** or **Microsoft Entra ID** <br>

    a. For **Microsoft Entra ID**: <br>
        1. **Authentication Type**, select **Oauth2.0(authorization code)**.<br>
        2. Enter the Client ID and Client Secret you copied when you created the Microsoft Entra ID app.<br>
        3. Select **Sign In**. You should get a **Connection successful** message. <br>

   b. For **SharePoint Provider (retiring soon)**: <br>
       1. In **Authentication Type**, select **Oauth2.0(client credentials)**. <br>
       2. Enter the Client ID and Client Secret you copied when you created the SharePoint app. <br>
       3. Select **Test Connection**. You should get a **Connection successful** message.

To control access on a file level, enter Microsoft Entra users or groups.

:::image type="content" source="media/csv-connector/csv-connector-acl.png" alt-text="Access control list with user and group included." lightbox="media/csv-connector/csv-connector-acl.png":::

### For an ADLS source

1. In the Data Source settings, select **Azure Data Lake Storage(ADLS)** as your datasource.
2. In **Primary storage connection string**, enter the connection string you copied.
3. Enter the **Container name** and **Filename**.
4. Select **Test Connection**. You should get a **The connection is successful** message.

:::image type="content" source="media/csv-connector/csv-connector-adls-data-source-settings.png" alt-text="CSV connector with Data Source Settings for an Azure Data Lake Storage source." lightbox="media/csv-connector/csv-connector-adls-data-source-settings.png":::

> [!NOTE]
> If your datasource contains multiple .csv files with the same headers, select **include all CSV files in location**.

To control access on a file level, enter Microsoft Entra users or groups.

:::image type="content" source="media/csv-connector/csv-connector-acl.png" alt-text="Access control list with user and group included." lightbox="media/csv-connector/csv-connector-acl.png":::

## Step 4: Multi-items delimiter (Optional)

If your source columns can take multiple values, enter a multi-item delimiter, a semicolon (;) for example.

## Step 5: Parsed properties settings

This page returns the first row from your .csv file as Source Properties. To modify the datatype, in the **Unique identifier** list select at least one option.

To control access on an item level, select columns mapped to allowed users and allowed groups. You should include two columns, AllowedUsers and AllowedGroups, in the .csv file. Each row should contain the Microsoft Entra IDs.

:::image type="content" source="media/csv-connector/csv-connector-acl-item-level.png" alt-text="Item level access control settings." lightbox="media/csv-connector/csv-connector-acl-item-level.png":::

> [!NOTE]
> The CSV Microsoft Graph connector supports file- or item-level access control. If both are enabled, only the file-level access control is applied.

## Step 6: Assign property labels

Follow the general [setup instructions](./configure-connector.md).

> [!NOTE]
> IconURL label is populated by default and the mapping cannot be changed.

## Step 7: Manage schema

Follow the general [setup instructions](./configure-connector.md).

## Step 8: Manage search permissions

- For file- or item-level access control, select **Only people with access to this data source**.
- Selecting **Everyone** allows everyone in your organization to see search results from this data source.

:::image type="content" source="media/csv-connector/csv-connector-search-permissions.png" alt-text="Search permission settings with only people with access to this data source selected." lightbox="media/csv-connector/csv-connector-search-permissions.png":::

## Step 9: Choose refresh settings

Follow the general [setup instructions](./configure-connector.md).

## Step 10: Review connection

Follow the general [setup instructions](./configure-connector.md).

<!---## Limitations-->
## Limitations

The following are known limitations of the CSV Microsoft Graph connector:
* Profile enrichment scenarios aren't supported at this time.

## Troubleshooting
After publishing your connection, you can review the status under the **Data sources** tab in the [admin center](https://admin.microsoft.com). To learn how to make updates and deletions, see [Manage your connector](manage-connector.md).

You can find troubleshooting steps for commonly seen issues [here](troubleshoot-csv-connector.md).

If you have issues or want to provide feedback, contact [Microsoft Graph | Support (https://developer.microsoft.com/en-us/graph/support).