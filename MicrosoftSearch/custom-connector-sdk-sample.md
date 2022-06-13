---
title: "Graph connectors SDK sample"
ms.author: rchanda
author: rchanda
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
description: "Graph connectors SDK sample"
---

# Build your first custom Microsoft Graph connector

Microsoft Graph connectors allow you to add your own data into Microsoft Graph and have it power various Microsoft 365 experiences.
This tutorial shows you how to use the Microsoft Graph connectors SDK to create a custom connector in C# and use it to power Microsoft Search. This tutorial uses a sample data appliance parts inventory for the Contoso Appliance Repair organization.

## How does the sample work?

Dataflow- diagram
Components and Architecture- diagram

The sample creates a gRPC server running your custom connector code on a virtual machine. A gRPC client from the Graph connector agent (Graph Connector Agent | Microsoft Docs) running on the same machine makes HTTP requests to the server for fetching the required response. The Graph connector agent takes care of ingesting the content into Microsoft Graph and other platform tasks.

## Develop your custom connector in C# using a template

### Prerequisites

1. [Visual Studio](https://visualstudio.microsoft.com/) 2019 or higher
2. .Net core SDK and runtime version 3.1

### Install the extension

1. Open visual studio and go to Extensions-> Manage extensions
2. Search for “GraphConnectorsTemplate” extension and download it
3. Close and relaunch Visual Studio to install the template
4. Go to File > New > Project and search for “GraphConnectorsTemplate”. Select the template and click Next.
5. Give a name to the project and click Next.
6. Choose .Net Core 3.1, give a name to the connector as “CustomConnector” and click Create.
7. The custom connector template project is created with skeleton code

### Create the custom connector

Before beginning to build the connector follow the steps given below to install nuget packages and create the data models that will be used in this connector.

#### Download the datasource files

1. Download the ApplianceParts.csv file from <TBD>

#### Install nuget packages

1. Right click on the project and select “Open in Terminal”

2. Run the below command

```dotnetcli
dotnet add package CsvHelper --version 27.2.1
```

#### Create Data models

1. Create a folder called "**Models**" under “CustomConnector” and create a file AppliancePart.cs under the folder.
2. Paste the following code in AppliancePart.cs

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel.DataAnnotations;
using System.Text;

namespace CustomConnector.Models
{
    public class AppliancePart
    {
        [Key]
        public int PartNumber { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public double Price { get; set; }
        public int Inventory { get; set; }
        public List<string> Appliances { get; set; }
    }
}

```
