---
title: "Microsoft Graph connectors FAQ"
ms.author: gladysa
author: gladysaj
manager: brian.j
ms.audience: Admin
ms.topic: reference
ms.service: mssearch
ms.localizationpriority: medium
ms.date: 09/11/2024
description: "Get answers to frequently asked questions about Microsoft Graph connectors"
---

# Microsoft Graph connectors FAQs

## 1. What are Microsoft Graph connectors?
Microsoft Graph connectors increase the discoverability and engagement of your enterprise data by deeply integrating your data into the Microsoft 365 Copilot experience. With Microsoft Graph connectors, you can make the most of your external data for functions like enriched data analysis, giving Copilot the ability to access and summarize your diverse datasets from different sources, enabling more comprehensive insights.
For more information, see [Microsoft Graph connectors overview](/graph/connecting-external-content-connectors-overview)

## 2. How do I set up a Microsoft Graph connector?
There are three main steps to set up a Microsoft Graph connector:

1. Create a connection.
2. Register your schema.
3. Ingest your content to the Microsoft Graph. Each item is sent with properties that match the schema you registered to power your content as discoverable in Microsoft 365 App.
For more information, see [Set up Microsoft Graph connectors in the Microsoft 365 admin center](/microsoftsearch/configure-connector).

## 3. Can I edit the query string once the connection is published?
Currently, the capability to edit the query string once the connection is published isn't supported. You need to create a new connection. However, the editability of the query string as a feature is in the roadmap and targeting availability by the end of CY24H2.
> [!NOTE]
> * As of publish date, query strings are available for ServiceNow Knowledge, ServiceNow Catalog, Confluence Cloud.

## 4. How do Microsoft Graph connectors work Microsoft 365 Copilot?
Microsoft Graph connectors allow external content to be stored in Microsoft Graph, enabling a way to surface external content in various Microsoft 365 experiences. This integration allows for Microsoft 365 Copilot to access and summarize your diverse datasets from different sources, enhancing the ways your users are already searching for answers.
For more information, see [Build Microsoft Graph connectors for Microsoft Copilot for Microsoft 365](/microsoft-365-copilot/extensibility/overview-graph-connector)

## 5. Is my data secure with Microsoft Graph connectors?
Yes, one crucial aspect of bringing content into Microsoft 365 is maintaining security and data access controls. When implementing Microsoft Graph connectors, you map existing access control lists to objects in Microsoft 365 and Microsoft Entra ID, ensuring that only individuals with the right permissions can access the content.

## 6. Where is the data stored when it is in Microsoft? 
When data enters the Microsoft cloud through the Graph connectors platform, it is automatically stored in the same region where the customer's Microsoft 365 tenant is located. We would also be adding options for customers to override the default region (upcoming feature).
**Learn More:** [Where your Microsoft 365 customer data is stored](/microsoft-365/enterprise/o365-data-locations)

## 7. Is the data ingested into Microsoft Graph connections encrypted? What encryption algorithm is used?  
Yes, the data is encrypted. Here are the details: 

- **Data at rest (in customer's master store):** Encrypted using DEK (Data Encryption Key) & KEK (Key Encryption Key) supplied to the partner. 
- **Data in transit:** Secure tunnel. 
- **Data at rest (in Office 365):** Encrypted using Office 365 encryption key by default (customers can provide their own encryption key) 
- Learn more about encryption in [Microsoft cloud](/purview/office-365-encryption-in-the-microsoft-cloud-overview) 

## 8. If customer data were already encrypted, would Microsoft now have access to the document encryption keys?
No, Microsoft would not have (or need) access to partner encryption keys. Content in the Microsoft cloud would be encrypted using Office 365 encryption keys by default. Customers can provide their own encryption key. For more information, see [Service encryption with customer key](/purview/customer-key-overview).

## 9. How long are copies of the customer content retained for when in Microsoft?
We adhere to a general Microsoft 365 data retention period. For more information, see [Data retention, deletion, and destruction in Microsoft 365](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview).

## 10. What are the best practices to test a connection?
- Create users in the test environment for ACL testing.
- Ensure you're using the right credentials to test the tenant.
- Ensuring users are assigned to the test tenant for staged rollouts and test for only those users.
- Use the [Index browser](/microsoftsearch/configure-connector) to verify if an item is indexed.

## Connectors specific FAQs

## 1. What are Microsoft offered Graph connectors?
Microsoft offered connectors are pre-built connectors provided by Microsoft that allow you to integrate various third-party content sources into Microsoft 365. These connectors help you bring external data into Microsoft 365, making it searchable and accessible within your organization. **Learn more:** [Microsoft Graph connectors gallery](/microsoftsearch/connectors-gallery)

## 2. What are some examples of Microsoft-built connectors?
Some examples of Microsoft-built connectors include connectors for popular services like Salesforce, ServiceNow, Confluence, and many others. These connectors enable you to integrate data from these services into Microsoft 365, enhancing your organization's ability to search and access this information and power Microsoft 365 Copilot experiences. **Learn more:** [Microsoft Graph connectors gallery](/microsoftsearch/connectors-gallery)

## 3. What are the benefits of using Microsoft-built connectors?
Microsoft-built connectors provide several benefits, including: 

- **Simplified integration:** Microsoft-built connectors are pre-built and ready to use, reducing the time and effort required to integrate external data sources. 
- **Enhanced searchability:** By bringing external data into Microsoft 365, Microsoft-built connectors make it easier for users to search and access this information. 
- **Improved productivity:** With Microsoft-built connectors, users can access all relevant information from within Microsoft 365, reducing the need to switch between different applications and platforms.

## 4. What are Microsoft Graph custom connectors? 
Microsoft Graph custom connectors allow you to integrate your own data sources into Microsoft Graph, enabling you to bring external data into Microsoft 365 experiences. It helps in making your data searchable and accessible within your organization. For more information, see [Microsoft Graph connectors overview](/graph/connecting-external-content-connectors-overview#get-started-with-custom-connectors).

## 5. How do I build a custom Microsoft Graph connector?
To build a custom Microsoft Graph connector, you can use the Microsoft Graph API. The API provides full control over the connection. **Learn more:** [Build your first custom Microsoft Graph connector](/graph/connecting-external-content-build-quickstart)

## 6. What are the prerequisites for creating a custom connector?
To create a custom connector, you need a Microsoft work or school account with the Global administrator role, and access to a Microsoft 365 tenant. If you don't have a Microsoft 365 tenant, you might qualify for one through the [Microsoft 365 Developer Program.](/office/microsoft-365-developer-program) **Learn more:** [Build your first custom Microsoft Graph connector](/graph/custom-connector-sdk-sample-create#prerequisites)

## 7. What is the difference between full crawl and incremental crawl?
**Full Crawl:** 
- Crawls the entire data source.
- Updates the index with all items.
- Reflects any deletions from the data source in the index.
- Updates the permissions.  

**Incremental crawl:**
- Only updates items that changed since the last crawl.
- Doesn't handle deletions, so items removed from the data source remain in the index. 
- Incremental crawls do not currently support processing of updates to permissions. 

For more details on crawl schedules and refresh settings: [Microsoft Graph connectors refresh settings](/microsoftsearch/configure-connector#step-8-refresh-settings)

## 8. Why don’t we get results to show up in Microsoft Search?
There could be several reasons why results are not displayed in Microsoft Search after configuring the Microsoft Graph connector. Here are some common issues and troubleshooting steps: 

- **Indexing delays:** Sometimes, it takes a while for the data to be indexed and displayed in search results. It can vary based on the volume of data and the complexity of the data source.
- **All vertical setting:** Ensure *“include results in All vertical”* is enabled. It should be enabled by default for Microsoft-built Graph connectors. For custom-built and third-party Microsoft Graph connectors, it needs to be enabled explicitly. 
- **Permissions issues:** Ensure that the correct permissions are set for the data source. If the permissions are not configured correctly, the data might not be accessible for indexing.
- **Configuration Errors:** Double-check the configuration settings of the Graph connector. Any misconfiguration can lead to issues with data indexing and search results.
- **Staged Rollout:** If you are using a [staged rollout](/microsoftsearch/staged-rollout-for-graph-connectors), validate which users are in the staged rollout. If staged rollout is no longer needed, you can end the staged rollout and make the connection available to all applicable users.
- **Supported file types and sizes:** Verify that the file types and sizes are supported by the Graph connector. Unsupported file types or sizes might not be indexed.
- **Custom Verticals:** Creating a custom vertical for each data source can help in troubleshooting and ensuring that the data is indexed correctly.

> [!NOTE]
> * If you have checked these common issues and are still facing problems, contact [Microsoft Graph | Support](https://developer.microsoft.com/en-us/graph/support). 

## Microsoft Graph Connector Agent (GCA) specific 

## 1. How does GCA interact with its system, and where is the indexed data stored?
The agent is installed on premises and needs access to the data source. Once the account is authorized, the agent crawls the data and talks to Graph connector services to push data to the index. The data indexed through Graph connectors sit at the same place.

## 2. Where should the Microsoft Graph Connector Agent be installed?
The agent should be installed on a machine that is on the same network as the data source, not necessarily the same machine hosting the data source. The data source URL must be accessible from the GCA machine.

## 3. Why does GCA require the ExternalConnection.ReadWrite.OwnedBy permission?
This permission allows GCA to read and write external connection settings on behalf of the Admin, but it can't access or modify anything beyond its granted permissions.

## 4. Can GCA be installed on multiple servers, and does the service run on both?
Yes, GCA can be installed on multiple machines, for multiple connections. One GCA can handle multiple connections. The crawl performance depends on the number of connections used for one GCA, crawl frequency, number of items etc. We recommend using not more than 3 connections per agent.