---
title: "Graph connectors SDK sample overview"
ms.author: rchanda
author: rchanda1392
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.date: 06/29/2022
description: "Graph connectors SDK sample overview"
---

# Build your first custom Microsoft Graph connector

Microsoft Graph connectors allow you to add your own data into Microsoft Graph and have it power various Microsoft 365 experiences.
This tutorial shows you how to use the Microsoft Graph connectors SDK to create a custom connector in C# and use it to power Microsoft Search. This tutorial uses a sample data- appliance parts inventory in a CSV file for the Contoso Appliance Repair organization.

>[!Note]
>Follow the steps mentioned [here](/MicrosoftSearch/custom-connector-sdk-other-languages) if you wish to develop your connector in languages other then C#.

## How does the sample work?

![Architecture of sdk based connectors](media/connectors-sdk/architecture.png)

The sample creates a gRPC server running the custom connector code on your virtual machine. A gRPC client from the [Graph connector agent](/microsoftsearch/graph-connector-agent) running on the same machine makes requests over gRPC to the server for fetching the required response. The Graph connector agent takes care of ingesting the content into Microsoft Graph and other platform tasks.

Follow the steps mentioned in the upcoming section to understand how to build your first custom connector.
