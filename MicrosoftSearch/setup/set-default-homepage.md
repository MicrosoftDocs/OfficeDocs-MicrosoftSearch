---
title: "Set default homepage"
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
ms.date: 12/20/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
ms.assetid: c020bd72-9906-4dfd-bc77-57287f5927ce
description: "Learn how to set Bing as the default homepage for your company with Microsoft Search in Bing."
---

# Set default homepage

Configuring the default browser, default search engine, and default homepage will help your users discover Microsoft Search in Bing capabilities, encourage more usage, and provide a smoother experience.
  
To set the default homepage for your organization, follow the steps below.
  
## Internet Explorer

### Internet Explorer 5.0 or later

1. Open the Group Policy Management Console (gpmc.msc) and switch to editing any existing policy or creating a new one.
    
2. Navigate to **User Configuration\Preferences\** **Control Panel Settings\Internet Settings**.
    
3. Right-click on **Internet Settings** and select **Internet Explorer 10**.
    
    > [!NOTE]
    > You need to select the option of Internet Explorer 10 to apply the settings for Internet Explorer 11 as the same settings apply to Internet Explorer 11. 
  
4. Settings which are underlined in red are not configured at the target machine, while settings underlined in green are configured at the target machine. To change the underlining, use the following function keys:
    
    F5 - Enable all settings on the current tab
    
    F6 - Enable the currently selected setting
    
    F7 - Disable the currently selected setting
    
    F8 - Disable all settings on the current tab
    
5. Press **F8** to disable all settings before configuring anything. The screen should look like this: 
    
    ![F8 screen](../media/2fd55755-5007-4e33-a795-c42ce2fcef4a.jpg)
  
6. Press **F6** on the Home page setting and enter [https://www.bing.com/business?form=BFBSPR](https://www.bing.com/business?form=BFBSPR)
    
7. Enforce the resultant GPO by linking it to the appropriate domain.
    
> [!NOTE]
> Users will be able to change the homepage after this policy is set. 
  
## Microsoft Edge

### Windows 10, Version 1511 or later

1. Open the Group Policy Management Console (gpmc.msc) and switch to editing any existing policy or creating a new one.
    
2. Navigate to **Administrative Templates\Windows Components\Microsoft Edge**
    
1. Double-click **Configure Start** pages, set it to **Enabled**, and enter https://www.bing.com/business
    
3. Enforce the resultant GPO by linking it to the appropriate domain.
    
> [!CAUTION]
> Users won't be able to change the search provider after this policy is set. 
  
## Google Chrome

### Windows XP SP2 or later

The latest ADMX files for different versions of Windows can be found [here](https://support.microsoft.com/en-in/help/3087759/how-to-create-and-manage-the-central-store-for-group-policy-administra).
  
If the settings described in this section can't be found inside of GPMC, download the appropriate ADMX and copy them to the [central store](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-vista/cc748955%28v%3dws.10%29). Central store on the controller is a folder with the following naming convention:
  
 **%systemroot%\sysvol\\<domain\>\policies\PolicyDefinitions**
  
Each domain your controller handles should get a separate folder. The following command can be used to copy the ADMX file from the command prompt:
  
 `Copy <path_to_ADMX.ADMX> %systemroot%\sysvol\<domain>\policies\PolicyDefinitions`
  
1. Open the Group Policy Management Console (gpmc.msc) and switch to editing any existing policy or creating a new one.
    
2. Make sure the following folders appear in the Administrative Templates section of both User/Computer Configuration: Google Chrome and Google Chrome - Default Settings (users can override).
    
  - The settings of the first section are fixed and the local administrator won't be able to change them.
    
  - The settings of the latter section of policies can be changed by users in their browser settings.
    
3. Navigate to **\<Computer/User Configuration\>\Administrative Templates\Google Chrome - Default Settings\** ** **Home Page**.**
    
1. Double-click **Use New Tab Page as homepage**, and set it to ** **Enabled**.**
    
4. Navigate to **\<Computer/User Configuration\>\Administrative Templates\Google Chrome - Default Settings\** ** **New Tab Page**.**
    
1. Double-click **Configure the New Tab Page URL**, set it to **Enabled**, and enter [https://www.bing.com/business?form=BFBSPR](https://www.bing.com/business?form=BFBSPR)
    
5. Enforce the resultant GPO by linking it to the appropriate domain.
    
Users will be able to change the home page after this policy is set.
  
## See also

[Set default search engine](set-default-search-engine.md)
  
[Set default browser](set-default-browser.md)
  

