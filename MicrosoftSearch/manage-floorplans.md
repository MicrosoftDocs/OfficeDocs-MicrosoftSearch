---
title: "Manage floor plans"
ms.author: rasrivas
author: rasrivas
manager: tonytha
ms.date: 11/01/2019
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "The floor plans feature in Microsoft Search helps users find people, offices, and other amenities within a building."
---
# Manage floor plans

Microsoft Search floor plans help users find people and meeting rooms within a building. Floor plans answer these questions:
- Where is Allan Deyoung's office?
- Where is meeting room C1?

![Floor plan map pinpointing the user's office location within the building.](media/floorplans-officelocation.png)

To make it easy to find answers to questions like these, information about an organization's buildings, offices, and facilities needs to be available and made searchable. Larger organizations usually have facilities or space management teams and might already have this info available. In a smaller organization, the Search admin might have to create and add it.

## 48 hours before you begin
Before you start to upload floor plans, you need to index the users' office locations. Depending on the size of your organization, it can take up to 48 hours to complete. If you ignore this step, you get errors while performing the procedure.

![Screen capture of floor plans page with "Microsoft needs to gather and organize office locations before you can upload floor plans" notice.](media/floorplans_hydrationstep.png)

In the Microsoft 365 [admin center](https://admin.microsoft.com), go to **Settings** > **Microsoft Search** > **Floor plans**, and then select **Get started**.

If you don't see this notice, then you or someone in your organization has already initiated this step.

## Things to consider
To help users to find information about offices and building facilities, you need to add:

|Consideration     |Why is this important?  |
|---------|---------|
|Building location    |    You'll need to add each building into Microsoft Search locations. You should come up with a standard naming format for each building. You can add the building by using a street address or map coordinates.     |
|**Office** property on all user accounts     |    Each user account needs to have the **office** property with their office location. And office locations should follow a standard format and include building, floor and room info.   <br> In Azure AD, this property is called **PhysicalDeliveryOfficeName**.    |
|Floor plan file in DWG format     |   You need a separate floor plan for each floor or wing of your building and include the office information in the same format that you used in the user's Office property. The file needs to be in AutoCAD drawing DWG format. |

For more information, see [Best practices for Microsoft Search floor plans](floorplans-bestpractices.md).

## Building location

Identify the buildings that need to be added as locations. The location address and map coordinates of a building are the first point of identification. If the building isn't added yet as a location, the admin needs to add it. See [Manage Locations](manage-locations.md) for more details.

## Floor plans files

After a building is identified, you can add its floor plans. All floor plan files must be in DWG format. If your organization doesn't already have them, you need to create the floor plans in a DWG-compatible app. Floor plans must correctly map all rooms, including conference or meeting rooms, restrooms, kitchens, mail rooms, and other facilities on each floor of the building to enable search.

### Office locations

To be mapped to floor plans, all office locations and employee office data must be in the user's account. In the floor plan, the office locations must be unique and cannot repeat. For example, if two people share office 2/1173, **2/1173** can only have one unique instance in your floor plans, but the user accounts in Azure AD will both have the same office location.

![floorplans-peoplecard.png](media/floorplans-peoplecard.png)

 > [!Note] 
 > When a user searches for a room or office location of a colleague, the room numbers in floor plans are matched with office locations in Azure AD. If a match is found, then the map is shown.

## Add floor plan

 The first time you go to floor plans, you might see a note at the top of the page that says, *Microsoft needs to gather and organize office locations before you can upload floor plans*. Select **Get started** to index your Azure AD office locations. 

1. In the [admin center](https://admin.microsoft.com), go to **Settings** > **Microsoft Search** >**Floor plans**, and then select **Add floor plans**.
4. Select the building in the drop-down and select **Next**. If the building isn't listed, you need to add it in Locations. See [Manage Locations](manage-locations.md) for more info.
6. Select **Upload files**, and then select the floor plan you want to upload. 
1. After the file uploads successfully, you need to identify how the floor number or wing is represented. 
7. Enter the code that identifies the building. The building code can be found on the user's account in the **Office location** property. For example, if the user's office location is **2/1173**, then building code is **2**. 
9. Review and identify the location patterns for all uploaded floor plans, and then select **Next**.
10. When you're ready, select **Publish** to make the floor plan searchable.

> [!Note] 
> When a floor plan is in a draft state, it's incomplete. A draft lets stakeholders coordinate in uploading and creating floor plans. It also allows you to deploy floor plans in stages.

## Edit floor plans

1. In the [admin center](https://admin.microsoft.com), go to **Settings** > **Microsoft Search** > **Floor plans**. 
1. Select **Published** or **Draft**, select the floor plan you want to change, and then select **Edit**.
5. Make your changes, and then select **Save**.

## Troubleshoot errors

You can't go to the next step of defining floor, wing, and room information until all errors are fixed. The following table file upload error messages and actions for fixing the issues.

| Error message   | Type    | Action       |
|:----------------| :--------- | :-------------- |
| Unable to read CC_1.dwg. Please re-upload or delete the floor plan. | Error |  Try uploading the file again. If that doesn't work, delete the file, and then try again. |
| There are two files named CC_1.dwg. Please delete one of them or re-upload with another name.| Error | If the file name is incorrect, make the file name unique by adding floor or wing information, and then upload the file again. <br><br>If you accidentally added the same file twice, just delete it. |
| No data found. | Error | Check your file to make sure it's the correct one, and then upload it again, or delete it. |
| External references are missing in this file. Either upload "CC_1_furniture.dwg" or delete this file. | Warning | Upload external reference files or delete.|
| Could not read room numbers or tags in the DWG file. Please delete  this file. | Warning | Check your DWG file to make sure the data is included, and then delete the file and try again. |
