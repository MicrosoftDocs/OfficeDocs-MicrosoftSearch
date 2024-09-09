---
ms.date: 06/17/2024
title: "Enhancing Microsoft Copilot Discovery with Graph Connector Content"
ms.author: souravpoddar
author: souravpoddar001
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
description: "Enhance the discoverability of Microsoft Graph Connector content within Microsoft Copilot."
---

# Enhancing Microsoft Copilot Discovery with Graph Connector Content

This document provides guidance on utilizing connection names and descriptions to enhance the likelihood for discoverability of Graph Connector content within Microsoft Copilot. Choosing a meaningful connection name and descriptions can inform Microsoft Copilot that there is pertinent content and information in a connection that addresses the user's request.

## Connection name

Pay attention to assigning a **representative and concise name** to each connection. This name should reflect the content's nature and intended use, facilitating users in easily identifying and accessing the relevant information.

## How to modify the description

### Microsoft-built connectors

For Microsoft-built connectors, you have the flexibility to **modify the connection name and description** in the admin portal at any time to reflect updates or changes in the content. These modifications are swiftly propagated to the system, typically within minutes.

   1. Go to the M365 Admin portal. In the navigation pane, select **Settings**, and then select **Search & intelligence**. 
   2. Select the [Data sources tab](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/Connectors).
   3. Select the connector that you would like to update the description for and click 'Edit' at the bottom of the right panel.
      ![Connection details pane](/MicrosoftSearch/media/connection-details-pane.png)

   4. In the 'Name and ID' step, you will find the description field. Add a description that best fits your organization's scenarios.
      ![Update the connection description](/MicrosoftSearch/media/update-the-connection-description.png)

   >[!Note]
   >1. Microsoft Graph Connectors for Jira, ServiceNow Tickets, ADO Work Items, and Salesforce have a default description tailored to the generic use of the connectors.
   >2. We still advise reviewing and modifying the descriptions to tailor them to the specific terms/language used by your organization.
   >3. For on-prem connectors, the connector description must be updated using the connector API. See more information here: [Microsoft Graph connector agent | Microsoft Learn](/MicrosoftSearch/graph-connector-agent)

   ### Good practices to write a connector description

   The connection description serves as a crucial element in aiding users to locate the desired content. Make sure that the following elements are present:
   * A brief overview of the content type. 
   * The scope of the content available within the connection. 
   * Keywords that users might employ to find this content (ex. _Tickets_, _Wiki_, _Knowledge Base_, _How to_, etc.).
   * Alternative names for the connection that users might be familiar with. 

#### Examples of connection names and description
Here are three examples of effective connection names and descriptions: 

1. **JIRA**: _This connection to Jira contains tickets to track issues related to software development and business project management. Jira may also be used for service desk tickets, product management, and other daily work item management. It is used to run scrums and track progress on initiatives, especially within engineering and product teams._

   _Keywords - Issues, Bugs, Tasks, Sub-tasks, Epic, User Story, Tickets, Backlog, Atlassian Jira_
2. **ServiceNow Tickets**: _This connection is used to manage and track customer requests and IT incidents. Businesses use this tool to enhance their service delivery and ensure issues are resolved on time._

3. **ADO Work Items**: _This connection to Azure DevOps Work items contains tickets to track software development and business projects. It is used by engineering and product teams to track daily work, run scrums and track progress on initiatives._

   _Keywords - Work items, Bugs, Tasks, Epic, User Story, Tickets, Backlog, Issue, ADO, Azure DevOps_

4. **Salesforce**: _Salesforce CRM stores a wide range of data to support various business functions. Types of data stored in Salesforce CRM include common record categories such as Leads, Accounts, Contacts, Opportunities, and Cases. Salesforce CRM's data model is designed to make data understandable and accessible, representing database tables as objects, columns as fields, and rows as records._

   _The content in this connection can also be referred to as SFDC, Salesforce data or Salesforce Sales cloud._
