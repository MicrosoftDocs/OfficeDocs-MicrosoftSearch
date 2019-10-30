---
title: "Best practices for Microsoft Search floor plans"
ms.author: anfowler
author: adefowler
manager: shohara
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Best practices for Microsoft Search floor plans"
---
# Best practices

To successfully implement Microsoft Search floor plans, you need to coordinate three pieces of data:

- **Building location data**: What format and how to add?
- **Floor plan map in DWG format**: How to view and what data should it contain for maximum success?
- **Employee office location in [Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/)**: What format to use and how to add? <br>

This article discusses the best practices for deploying Microsoft Search floor plans.

## Building location data
Before you add floor plans, you need to add your buildings to Microsoft Search locations. Provide the required building data shown in the following table:

|Required building data  |Example  |
|---------|---------|
|Name     |    Building 1, New York City     |
|Street address     |     123 Any Avenue, New York City, NY 10118  |
|Latitude-longitude  (optional)   |    40.760539, -73.975341      |
|Keywords     |    New York Office, Building 1, main office, headquarters     |

You can add many buildings at a time by using the **Import** feature in the **Locations** tab instead of adding locations one at a time. With the **Import** feature, you can specify the latitude-longitude. For more information, see [Manage locations](manage-locations.md).

## Floor plan map in DWG format
To build maps in Microsoft Search, you need to upload floor plans in DWG format with specific information. To learn how to create and view DWG-formatted files, see [DWG Viewers](https://www.autodesk.in/products/dwg). 

Floor plan maps display four elements:

1. **Room numbers**: In the following example, room numbers are defined as **B1 1001** and **B1 1002**. **B1** is the building code, and 1001 contains the floor number **1** and the office number **001**.
1. **Room layouts.**: To help clarify details when multiple users share an office, you can define layouts like chairs and desk.
1. **Room types**: Some examples include office, corridor, open area, and toilet.
1. **Asset info**: If users are in an open space, you can denote which desk they sit at. In this example, the desks are denoted by **TB1** and **TB2**.

![Simple office map showing how to label room numbers, assets, and room types](media/Floorplans-LayoutwithCallouts.png)

In this diagram, room numbers are the most important item. They're mapped to a person’s office location on their user account as shown in the following image.

![Overview tab of the people search result card showing the user's details, including office location](media/floorplans-peoplecard.png)

This information is stored in Azure AD in the **PhysicalDeliveryOfficeName** property. In the Microsoft 365 [admin center](https://admin.microsoft.com), it’s called the **Office** property and can be added in Active users.

### DWG files
Microsoft Search requires floor plan files in DWG, which is format an AutoCAD drawing format. The files must contain **layout** and **label** data. **Room numbers** are the most important labels for floor plans.

We recommend that you create your office numbering system with the exact match method shown in the following table. But you are not limited to that labeling. For example, if the user's office location in Azure AD is "B1 1001", you have the following options for labeling the room number in the DWG file.

|Match  |Layout  |
|---------|---------|
|Exact match to office location (Recommended) <br> **B1 1001** <br> Building code: B1<br>Floor: 1 <br>Room number: 001    |    ![Single office floor plan with the office number "B1 1001".](media/floorplans-layoutexactmatch.png)     |
|Match floor and room number <br> **1001**<br>Floor: 1 <br>Room number: 001    |   ![Single office floor plan with the office number "1001".](media/floorplans-layoutfloorroom.png)   |
|Match room number only <br> **1**<br>Room number: 1        |    ![Single office floor map with the office number "1"](media/floorplans-layoutroomonly.png)     |

## User account office location
To map an employee’s location, the room numbers in DWG files are mapped to office locations on the user’s account in Azure AD. The **Office location** property needs to match the Office location information in the DWG file:

|Best practice  |Examples |
|---------|---------|
|Use building code, floor, and room number     |   As a best practice, Office locations should include the building code, floor, and room number. This give you the best chance to make exact matches.     |
|Use a separator after building codes and floors     |  Building codes should be separated from the floor and room numbers using a separator or a space. Examples:<br> B1 1001<br> B1/1001 <br> B1-1001   |
|Room number always comes after the building code, wing, and floor information     |  If room number is 1001, then set office location to B1 1001, B1/1001, B1-1001. <br> If the room number is F1-001, then set office location to B1 F1-001, B1/F1-001. <br> If the room number is 1, then set AAD location to B1 1001, B1/1001 or B1-F1-001.       |
|

## Next steps
[Manage locations](manage-locations.md)<br>
[Manage floor plans](manage-floorplans.md)