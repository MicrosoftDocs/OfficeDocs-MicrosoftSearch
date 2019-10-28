---
title: "Best practices for Microsoft Search floor plans"
ms.author: anfowler
author: adefowler
manager: shohara
ms.date: 10/08/2019
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
# Best practices for Microsoft Search floor plans

To successfully implement Microsoft Search floor plans, you need to coordinate 3 pieces of data:
- Building location data: What format and how to add?
- Floor plan map in DWG format: How to view and what data should it contain for maximum success?
- Employee office location in Azure AD: What format to use and how to add?
This article discusses the best practices for deploying Microsoft Search floor plans.

## Building location data
Before you can add floor plans, you to add your buildings to Microsoft Search locations. To do that, you’ll need to know this information:

|Required building data  |Example  |
|---------|---------|
|Name     |    Building 1, New York City     |
|Street address     |     123 Any Avenue, New York City, NY 10118  |
|Latitude-longitude  (optional)   |    40.760539, -73.975341      |
|Keywords     |    New York Office, Building 1, main office, headquarters     |

If you are adding many buildings at a time, use the **Import** feature in the **Locations** tab rather than adding locations one at a time. The import feature lets you specify the latitude-longitude. The **Add floor plans** wizard only lets you add the street address. For more information, see [Manage locations].

## Floor plan map in DWG format
Microsoft Search needs you to upload floor plans in DWG format with very specific information. For more information about creating and viewing DWG formatted files, see [DWG Viewers](https://www.autodesk.in/products/dwg). 

For example in the following diagram, there are a few things that should be pointed out.
1. Room numbers are defined as “B1 1001”, “B1 1002”. 
 Where B1 is the building code, and 1001 contains the floor number "1" and the office number "001".
1. Room layouts - Defining layouts such as chairs and desks can help when multiple users share an office.
1. Room types – Office, corridor, open area, toilet.
1. Asset info – For example, if users are in an open space, you can denote which desk they sit at. In this example, those are denoted by TB1, TB2.

![Simple office map showing how to label room numbers, assets, and room types.](media/Floorplans-LayoutwithCallouts.png)

In this diagram, room numbers are the most important item. This gets mapped to a person’s office location on their user account as shown below.
####insert outlook people card####

This information is stored in Azure AD in the **Office location** property. In the Microsoft 365 admin center, it’s called the “Office” property and can be added in Active users.

### Working with DWG files
Microsoft Search requires floor plans in DWG format. DWG is an AutoCAD format. The file must contain **layout** and **label** data. The labels MOST important for floor plans is **room numbers**. 

We recommend that you create your office numbering system using the exact match method as in the following table, but you are not limited to that labeling. For example, if the user's office location in Azure AD is "B1 1001", you have the following options for labeling the room number in the DWG file.


|Match  |Layout  |
|---------|---------|
|Exact match to office location (Recommended) <br> **B1 1001** <br> Building code: B1<br>Floor: 1 <br>Room number: 001    |    ![Single office floor plan with the office number "B1 1001".](media/floorplans-layoutexactmatch.png)     |
|Match floor and room number <br> **1001**<br>Floor: 1 <br>Room number: 001    |   ![floorplans-layoutfloorroom.png](media/floorplans-layoutfloorroom.png)   |
|Match room number only <br> **1**<br>Room number: 1        |    ![floorplans-layoutroomonly.png](media/floorplans-layoutroomonly.png)     |

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