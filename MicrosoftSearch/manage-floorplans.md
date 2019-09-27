---
title: "Manage floorplans"
ms.author: rasrivas
author: rasrivas
manager: tonytha
ms.date: 09/09/2019
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "The floorplans feature in Microsoft Search helps users find people, offices, and other amenities within a building."
---
# Manage floorplans

  ![Office location isn’t just a number with Microsoft Search.](media/floorplans-fig1.png "Office location.")

*Figure 1 – Office location isn’t just a number with Microsoft Search.*

The floorplans feature in Microsoft Search helps users find people, offices, and other amenities within a building. Floorplans answer users' queries such as:

1. Where is Allan Deyoung's office?
2. Where is conference room C1?
3. Where is the cafeteria in building 2?
4. Is there a pantry on this floor?
5. Are there open working spaces in this building?

To make it easy to find answers to queries like these, information about an organization's buildings, offices, and facilities needs to be available and made searchable. Larger organizations usually have a facilities or space management team who may already have this info available. In a smaller organization, the Search Administrator might have to create and add it. A Search Administrator can delegate this work and allow other employees or vendors to add floorplans and building information by designating them as Search Editors.
To enable users to find information about offices and building facilities, you need to add:

1. Locations for each building
2. Floorplans for each building in Autodesk DWG format
3. Standardized and unique nomenclature for identifying buildings and floors
4. Employees' locations to the room numbers mapped in Azure Active Directory (AAD)

 ![The office location data is defined in AAD as employee seat numbers.](media/floorplans-fig2.png "Office location data is defined in AAD.")

*Figure 2 – The office location data is defined in AAD as employee seat numbers.*

The field in AAD where seat numbers are stored is called ‘Office Location’.

### Step 1: Buildings and locations

Identify the buildings that need to be added as locations. The location address and map coordinates of a building are the first point of identification, and floorplans are associated with the building. If the building location (address) is already in AAD, the Search Administrator just needs to search for the building name and select it. If the building is not yet added as a location, the admin needs to add it. See Manage Locations for more details.

### Step 2: Floorplans

Once a building is identified, you can add its floorplans. All floorplans must be in DWG format. If your organization doesn't already have them, you'll need to create the floorplans in AutoCAD or another DWG-compatible app. Floorplans must correctly map all rooms, including conference or meeting rooms, restrooms, kitchens, mailrooms, and other facilities on each floor of the building to enable search.

### Step 3: Unique identification codes

Each building and floorplan must have a unique identification code. Buildings, floors, wings, and room numbers are used to uniquely identify office locations in AAD. You must use only one standardized pattern to define the office locations in a building. 

For example, your organization might standardize on a pattern where the first character identifies the building (A), followed by a number identifying the floor (1), and then a three-digit number identifying a room (119). 

In this example, A1/119 would uniquely identify room 119 on the first floor of Building A and B2/309 would uniquely identify room 309 on the second floor of Building B.
Whichever numbering system you decide upon needs to be followed consistently for all rooms, floors, and buildings of your organization.

![Office floorplan search.](media/floorplans-fig3.png "Office floorplan search.")

*Figure 3 – Office floorplan search*

### Step 4: Personnel and office data in AAD

All office locations and employee office data must be stored in AAD in order to be mapped to floorplans. All office locations must have unique values; that is, two or more people may sit in an open area that has an office location ID of B1/0001, but B1/0001 is a unique location and there is no other location with the same code in AAD.

 **Note:** When a user searches for a room or office location of a colleague, the room numbers in floorplans are matched with office locations in AAD. If a match is found, then the floor map is shown.
It can take several hours for new or changed floorplans to appear in search results.

## Add floorplan

  ![Specify the Floor and Wing or Zone that each file represents.](media/floorplans-fig4.png "Specify the Floor and Wing or Zone.")

*Figure 4 – Specify the Floor and Wing or Zone that each file represents.*

1. Log in using your admin credentials and go to Microsoft 365 admin center.
2. In the navigation pane, go to Settings and select Microsoft Search.
3. Select Floorplans tab.
4. Select Add floorplans to open the Add floorplans dialog.
5. Select the building in the dropdown and select Next. If the building is not listed in the dropdown, you can add it as a new location. See Manage Locations for more info.
6. Select Upload files and select the floorplan you want to upload. All floorplans must be in DWG format. You can upload multiple floorplans at the same time. After the file is uploaded, identify the floor and/or wing in the building that the floorplan is for.  

If a floorplan cannot be uploaded, an error messages should identify the issue and solution. For troubleshooting DWG file upload issues, see the Troubleshoot Errors section. The Next button will be disabled until all floorplans are successfully uploaded.

  ![Specify the office location that’s related to the seat numbers you assigned.](media/floorplans-fig5.png "Specify the office location.")

*Figure 5 – Specify the office location that’s related to the seat numbers you assigned.*

7. Preview the files. Preview allows the admin to see the floorplan that Microsoft Search users see and decide whether they want to continue with the upload. An admin might decide to cancel an upload if elements such as walls or furniture are missing. Selecting the Preview option also lists the total errors. Clicking opens the preview overlay, which allows them to see the floorplan. The admin can browse all floorplans, zoom in and out of the preview, and pan to see different parts of the floorplan in more detail.
8. Link office locations by adding AAD codes for each of the floorplans uploaded.
This helps define what the AAD code for a building might look like in the organization. Microsoft Search extracts the building code from AAD based on location and displays it for confirmation. If Microsoft Search is not able to extract the code, then the admin must specify the code. The Search Admin can determine the building code by looking at the address card of a person in that building.
9. Next, specify the location nomenclature. Here you define what each of the different characters or numbers in the code identifies. For example, the building code PS35/13/0124 identifies a building name and number (PS35), followed by a floor number (13th floor), and finally, the room number (0124). Microsoft Search tries to extract the pattern and displays it for confirmation. The Search Admin can determine the pattern by looking at the location information for an employee in the address card.
10. After associating a building with an AAD location and specifying location patterns for all uploaded floorplans, select Publish to add to the floorplans. Or you can save the plans as a draft for publishing later.

![When mapping is complete, you’re ready to go](media/floorplans-fig6.png "Mapping complete")

*Figure 6 – When mapping is complete, you’re ready to go*

 **Note:** A draft is a building for which floorplans or mapping is incomplete. A draft enables multiple people such as IT admins, business admins, and facility management teams to coordinate in uploading and creating floorplans. It also allows users to upload floorplans in stages.
11. In the Floorplans tab on the Microsoft Search home page, the published or saved draft floorplans are listed under Published or Draft.

## Edit floorplan

1. Log in using your admin credentials and go to Microsoft 365 admin center.
2. In the navigation pane, go to Settings and select Microsoft Search.
3. Select the Floorplans tab. The existing floorplans are listed under Published or Draft.
4. Select the floorplan you want and click Edit.
5. Edit the details and floorplans and save.

 **Note:** The draft facility is not available once the building is published. A Search Editor can still edit a published building, but they cannot make partial changes and save it to draft. They need to make the changes in one session. Any changes saved are shown in the Office location tab in the People card in Microsoft Search. A Search Editor can choose to unpublish a building, in which case the building is moved to the Drafts section and the details are not shown in the Office location tab.

## Troubleshoot errors

A Search Administrator cannot proceed to the next step of defining floor, wing, and room information until all errors are fixed. Here's a list of DWG file upload error messages and actions for fixing the issues.

| Error message   | Type    | Action       |
|:----------------| :--------- | :-------------- |
| Unable to read CC_1.dwg. Please re-upload or delete the floorplan. | Error |  Reupload or delete |
| There are two files named CC_1.dwg. Please delete one of them or re-upload with another name.| Error | Reupload, delete or add wing/section information |
| No data found. | Error | Reupload or delete |
| External references are missing in this file. Either upload "CC_1_furniture.dwg" or delete this file. | Warning | Upload external reference files or delete |
| Could not read room numbers or tags in the DWG file. Please delete  this file. | Warning | Reupload or delete |
