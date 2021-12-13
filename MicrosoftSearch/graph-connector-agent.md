--- 
title: "On-Premises Agent" 
ms.author: rusamai 
author: rsamai 
manager: jameslau 
audience: Admin
ms.audience: Admin 
ms.topic: article 
ms.service: mssearch 
ms.localizationpriority: medium 
search.appverid: 
- BFB160 
- MET150 
- MOE150 
description: "On-prem Agent" 
--- 

# Microsoft Graph connector agent

Using on-prem connectors require you to install *Microsoft Graph connector agent* software. It allows for secure data transfer between on-premises data and the connector APIs. This article guides you through the installing and configuring the agent.

## Installation

Download the latest version of the Graph connector agent from [https://aka.ms/GCAdownload](https://aka.ms/gcadownload) and install the software by using the installation wizard. Using the recommended configuration of the machine described below, the software can handle up to three connections. Any connections beyond that might degrade the performance of all connections on the agent.

Recommended configuration:

* Windows 10, Windows Server 2016 R2 and above
* [.NET Core Desktop Runtime 3.1 (x64)](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* 8 cores, 3 GHz
* 16 GB RAM, 2 GB Disk Space
* Network access to data source and internet through 443

After you install the agent, if your organization's proxy servers or firewalls block communication to unknown domains, please add below ones to the allow list.

1. *.servicebus.windows.net
2. *.events.data.microsoft.com
3. https://<span>login.microsoftonline.</span>com
4. https://<span>gcs.office.</span>com/
5. https://<span>graph.microsoft.</span>com/

>[!NOTE]
>Proxy authentication is not supported. If your environment has a proxy that requires authentication, our recommendation is to allow the connector agent to bypass the proxy.

## Create and configure an App for the agent  

First, sign in and note that the minimum required privilege on the account is search administrator. The agent will then ask you to provide authentication details. Use the steps below to create an app and generate the required authentication details.

### Create an app

1. Go to the [Azure portal](https://portal.azure.com) and sign in with admin credentials for the tenant.

2. Navigate to **Azure Active Directory** -> **App registrations** from the navigation pane and select **New registration**.

3. Provide a name for the app and select **Register**.

4. Make a note of the Application (client) ID.

5. Open **API permissions** from the navigation pane and select **Add a permission**.

6. Select **Microsoft Graph** and then **Application permissions**.

7. Search for "ExternalItem.ReadWrite.All", "Directory.Read.All" and "ExternalConnection.ReadWrite.OwnedBy" from the permissions and select **Add permissions**.

8. Select **Grant admin consent for [TenantName]** and confirm by selecting **Yes**.

9. Check that the permissions are in the "granted" state.

    :::image type="content" alt-text="Permissions shown as granted in green on right hand column." source="media/onprem-agent/granted-state.png" lightbox="media/onprem-agent/granted-state.png":::

### Configure Authentication

Authentication details can be provided using a client secret or a certificate. Follow the steps of your choice.

#### Configuring the client secret for authentication

1. Go to the [Azure portal](https://portal.azure.com) and sign in with admin credentials for the tenant.

2. Open **App Registration** from the navigation pane and go to the appropriate App. Under **Manage**, select **Certificates and secrets**.

3. Select **New Client secret** and select an expiry period for the secret. Copy the generated secret and save it because it won't be shown again.

4. Use this Client secret along with the Application ID to configure the agent. You cannot use blank spaces in the **Name** field of the agent. Alpha numeric characters are accepted.

#### Using a certificate for authentication

There are three simple steps for using certificate-based authentication:

1. Create or obtain a certificate
2. Upload the certificate to the Azure portal
3. Assign the certificate to the agent

##### Step 1: Get a certificate

The script below can be used to generate a self-signed certificate. Your organization may not allow self-signed certificates. In that case, use this information to understand the requirements and acquire a certificate in accordance to your organization's policies.

```powershell
$dnsName = "<TenantDomain like agent.onmicrosoft.com>" # Your DNS name
$password = "<password>" # Certificate password
$folderPath = "D:\New folder\" # Where do you want the files to get saved to? The folder needs to exist.
$fileName = "agentcert" # What do you want to call the cert files? without the file extension
$yearsValid = 10 # Number of years until you need to renew the certificate
$certStoreLocation = "cert:\LocalMachine\My"
$expirationDate = (Get-Date).AddYears($yearsValid)
$certificate = New-SelfSignedCertificate -DnsName $dnsName -CertStoreLocation $certStoreLocation -NotAfter $expirationDate -KeyExportPolicy Exportable -KeySpec Signature
$certificatePath = $certStoreLocation + '\' + $certificate.Thumbprint
$filePath = $folderPath + '\' + $fileName
$securePassword = ConvertTo-SecureString -String $password -Force -AsPlainText
Export-Certificate -Cert $certificatePath -FilePath ($filePath + '.cer')
Export-PfxCertificate -Cert $certificatePath -FilePath ($filePath + '.pfx') -Password $securePassword
```

##### Step 2: Upload the certificate in the Azure portal

1. Open the application and navigate to certificates and secrets section from left pane.

2. Select **Upload certificate** and upload the .cer file.

3. Open **App registration** and select **Certificates and secrets** from the navigation pane. Copy the certificate thumbprint.

:::image type="content" alt-text="List of thumbprint certificates when Certificates and secrets is selected in the left pane." source="media/onprem-agent/certificates.png" lightbox="media/onprem-agent/certificates.png":::

##### Step 3: Assign the certificate to the agent

If you used the sample script to generate a certificate, the PFX file can be found in the location identified in the script.

1. Download the certificate pfx file onto the Agent machine.

2. Double-click the pfx file to launch the certificate installation dialog.

3. Select **Local Machine** for store location while installing the certificate.

4. After installing the certificate, open **Manage computer certificates** through Start menu.

5. Select the newly installed certificate under **Personal** > **Certificates**.

6. Right click on the cert and select **All Tasks** > **Manage Private Keys** Option.

7. In the permissions dialog, select add option. It pops up a new window. Select 'Locations' option in it. Select the machine on which agent is installed among the list of locations shown and click **OK**.

8. In the user selection dialog, write: **NT Service\GcaHostService** and click **OK**. Don't click the **Check Names** button.

9. Click okay on the permissions dialog. The agent machine is now configured for agent to generate tokens using the certificate.

## Troubleshooting

### Installation failure

If the installation fails, check the installation logs by running: msiexec /i "< path to msi >\GcaInstaller.msi" /L*V "< destination path >\install.log". If the errors are not resolvable, reach support on MicrosoftGraphConnectorsFeedback@service.microsoft.com with the logs.

### Registration failure

If sign in to config app fails with error "Sign in failed. Please click on sign in button to try again." even after browser authentication succeeded, open services.msc and check if GcaHostService is running. If it is not, start it manually.

If the service fails to start with the error "The service did not start due to a logon failure", check if virtual account NT Service\GcaHostService has permission to log on as a service on the machine. Check [this link](/windows/security/threat-protection/security-policy-settings/log-on-as-a-service) for instructions. If the option to add user or group is greyed out in the Local Policies\User Rights Assignment, it means the user trying to add this account does not have admin privileges on this machine or that there is a group policy overriding this. The group policy needs to be updated to allow host service to logon as a service.

### Connection failure

If 'Test connection' action fails while creating connection with the error 'Please check username/password and the datasource path' even when the provided username and password are correct, ensure that the user account has interactive logon rights to the machine where Graph connector agent is installed. Refer the documentation about [logon policy management](/windows/security/threat-protection/security-policy-settings/allow-log-on-locally#policy-management) to check logon rights. Also ensure that the data source and the agent machine are on the same network.

If a connection fails with the error "1011: The Graph connector agent is not reachable or offline.", log in to the machine where agent is installed and start the agent application if it isn't running already. If the connection continues to fail, verify that the certificate or client secret provided to the agent during registration hasn't expired and has required permissions.
