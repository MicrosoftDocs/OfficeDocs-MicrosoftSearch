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

### Dataflow

diagram

### Components and Architecture

diagram

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

1. Download the ApplianceParts.csv file from \<TBD>

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

#### Update ConnectionManagementServiceImpl.cs

ConnectionManagementServiceImpl.cs has 3 methods to be implemented:

**ValidateAuthentication**
This method is used to validate the credentials and the datasource URL provided. We need to connect to the datasource URL using the credentials provided and return success if the connection succeeds or auth failure status if the connection fails.

1. Create a folder called "**Data**" under “CustomConnector” and create a file CsvDataLoader.cs in the folder.

2. Copy the following code to CsvDataLoader.cs:

    ```csharp
    using CsvHelper;
    using CsvHelper.Configuration;
    using CsvHelper.TypeConversion;
    
    using CustomConnector.Models;
    
    using System.Collections.Generic;
    using System.Globalization;
    using System.IO;
    
    namespace CustomConnector.Data
    {
        public static class CsvDataLoader
        {
            public static void ReadRecordFromCsv(string filePath)
            {
                using (var reader = new StreamReader(filePath))
                using (var csv = new CsvReader(reader, CultureInfo.InvariantCulture))
                {
                    csv.Context.RegisterClassMap<AppliancePartMap>();
                    csv.Read();
                }
            }
        }
    
        public class ApplianceListConverter : DefaultTypeConverter
        {
            public override object ConvertFromString(string text, IReaderRow row, MemberMapData memberMapData)
            {
                var appliances = text.Split(';');
                return new List<string>(appliances);
            }
        }
    
        public class AppliancePartMap : ClassMap<AppliancePart>
        {
            public AppliancePartMap()
            {
                Map(m => m.PartNumber);
                Map(m => m.Name);
                Map(m => m.Description);
                Map(m => m.Price);
                Map(m => m.Inventory);
                Map(m => m.Appliances).TypeConverter<ApplianceListConverter>();
            }
        }
    }
    
    ```

    The ReadRecordFromCsv method will just open the CSV file and read the first record from the file. We can use this to validate if the provided datasource URL (path of the CSV file) is valid. This connector is using anonymous auth, hence there is no validation of credentials here. If it is using any other auth type, the connection to datasource must be made using the provided credentials to validate the authentication.

3. Add the following using directive in ConnectionManagementServiceImpl.cs

    ```csharp
    using CustomConnector.Data;
    ```

4. Update the ValidateAuthentication method in ConnectionManagementServiceImpl.cs with the following code to call the ReadRecordFromCsv method of CsvDataLoader class

    ```csharp
    public override Task<ValidateAuthenticationResponse> ValidateAuthentication(ValidateAuthenticationRequest request, ServerCallContext context)
            {
                try
                {
                    Log.Information("Validating authentication");
                    CsvDataLoader.ReadRecordFromCsv(request.AuthenticationData.DatasourceUrl);
                    return this.BuildAuthValidationResponse(true);
                }
                catch (Exception ex)
                {
                    Log.Error(ex.ToString());
                    return this.BuildAuthValidationResponse(false, "Could not read the provided CSV file with the provided credentials");
                }
            }
    
    ```

**ValidateCustomConfiguration**
This method is used to validate any additional parameters required for the connection. This connector we are writing does not require any additional parameters, hence the validation is that the additional parameters should be empty.

1. Update ValidateCustomConfiguration method in ConnectionManagementServiceImpl.cs with the following code

    ```csharp
    public override Task<ValidateCustomConfigurationResponse> ValidateCustomConfiguration(ValidateCustomConfigurationRequest request, ServerCallContext context)
        {
            Log.Information("Validating custom configuration");
            ValidateCustomConfigurationResponse response;

            if (!string.IsNullOrWhiteSpace(request.CustomConfiguration.Configuration))
            {
                response = new ValidateCustomConfigurationResponse()
                {
                    Status = new OperationStatus()
                    {
                        Result = OperationResult.ValidationFailure,
                        StatusMessage = "No additional parameters are required for this connector"
                    },
                };
            }
            else
            {
                response = new ValidateCustomConfigurationResponse()
                {
                    Status = new OperationStatus()
                    {
                        Result = OperationResult.Success,
                    },
                };
            }

            return Task.FromResult(response);
        }

    ```

**GetDataSourceSchema**
This method is used to fetch the schema for the connector:

1. Add the following using directives in AppliancePart.cs

    ```csharp
    using Microsoft.Graph.Connectors.Contracts.Grpc;
    using static Microsoft.Graph.Connectors.Contracts.Grpc.SourcePropertyDefinition.Types;

    ```

2. Add the following method GetSchema in AppliancePart.cs class

     ```csharp
      public static DataSourceSchema GetSchema()
        {
            DataSourceSchema schema = new DataSourceSchema();

            schema.PropertyList.Add(
                new SourcePropertyDefinition
                {
                    Name = nameof(PartNumber),
                    Type = SourcePropertyType.Int64,
                    DefaultSearchAnnotations = (uint)(SearchAnnotations.IsQueryable | SearchAnnotations.IsRetrievable),
                    RequiredSearchAnnotations = (uint)(SearchAnnotations.IsQueryable | SearchAnnotations.IsRetrievable),
                });

            schema.PropertyList.Add(
                new SourcePropertyDefinition
                {
                    Name = nameof(Name),
                    Type = SourcePropertyType.String,
                    DefaultSearchAnnotations = (uint)(SearchAnnotations.IsSearchable | SearchAnnotations.IsRetrievable),
                    RequiredSearchAnnotations = (uint)(SearchAnnotations.IsSearchable | SearchAnnotations.IsRetrievable),
                });

            schema.PropertyList.Add(
                new SourcePropertyDefinition
                {
                    Name = nameof(Price),
                    Type = SourcePropertyType.Double,
                    DefaultSearchAnnotations = (uint)(SearchAnnotations.IsRetrievable),
                    RequiredSearchAnnotations = (uint)(SearchAnnotations.IsRetrievable),
                });

            schema.PropertyList.Add(
                new SourcePropertyDefinition
                {
                    Name = nameof(Inventory),
                    Type = SourcePropertyType.Int64,
                    DefaultSearchAnnotations = (uint)(SearchAnnotations.IsQueryable | SearchAnnotations.IsRetrievable),
                    RequiredSearchAnnotations = (uint)(SearchAnnotations.IsQueryable | SearchAnnotations.IsRetrievable),
                });

            schema.PropertyList.Add(
                new SourcePropertyDefinition
                {
                    Name = nameof(Appliances),
                    Type = SourcePropertyType.StringCollection,
                    DefaultSearchAnnotations = (uint)(SearchAnnotations.IsSearchable | SearchAnnotations.IsRetrievable),
                    RequiredSearchAnnotations = (uint)(SearchAnnotations.IsSearchable | SearchAnnotations.IsRetrievable),
                });

            schema.PropertyList.Add(
                new SourcePropertyDefinition
                {
                    Name = nameof(Description),
                    Type = SourcePropertyType.String,
                    DefaultSearchAnnotations = (uint)(SearchAnnotations.IsSearchable | SearchAnnotations.IsContent),
                    RequiredSearchAnnotations = (uint)(SearchAnnotations.IsSearchable | SearchAnnotations.IsContent),
                });

            return schema;
        }
  
     ```

3. Add the following using directive in ConnectionManagementServiceImpl.cs

    ```csharp
    using CustomConnector.Models;
    ```

4. Update the GetDataSourceSchema method in ConnectionManagementServiceImpl.cs with the following code

    ```csharp
    public override Task<GetDataSourceSchemaResponse> GetDataSourceSchema(GetDataSourceSchemaRequest request, ServerCallContext context)
        {
            Log.Information("Trying to fetch datasource schema");

            var opStatus = new OperationStatus()
            {
                Result = OperationResult.Success,
            };

            GetDataSourceSchemaResponse response = new GetDataSourceSchemaResponse()
            {
                DataSourceSchema = AppliancePart.GetSchema(),
                Status = opStatus,
            };

            return Task.FromResult(response);
        }

    ```

#### Update ConnectorCrawlerServiceImpl.cs
