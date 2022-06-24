---
title: "Graph connectors SDK TestApp"
ms.author: rchanda
author: rchanda
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
description: "Graph connectors SDK Test Application"
---

# About GraphConnectorAgentTest executable

The GraphConnectorAgentTest executable is a test utility to test the functionalities of the custom connector.
It doesn't create any connection or index any data into Microsoft’s index. This test utility runs only on the machine on which the agent is installed and doesn't make any connections to any external resource except the datasource being tested.
You can find the test application inside the "TestApp" folder present in your Graph connector agent installation folder.

You need to update the following config files to use this test utility:

**ConnectionInfo.json**: This file holds all information pertaining to the connection – the connector ID identifying the custom connector for which this connection is being created, the datasource URL, credentials to access the datasource, the schema associated with the connection, extra parameters for the connection.

You can find this config file inside the "Config" folder of the test application.

**CustomConnectorPortMap.json**: After creating the custom connector, add the mapping of the connector ID and the port on which it's running in this file. You can add multiple connector IDs and their corresponding port information in this file. Each unique connector should be running on a different port.

You can find this file in your Graph connector agent installation folder.

After creating the custom connector, add the mapping of the connector ID and the port on which it's running in the CustomConnectorPortMap.json.

![Port mapping graphics](media/connectors-sdk/port.png)

## Test scenarios

This test utility has three options:

**1. Testing the connectivity to the connector service**: This option is to verify that the connector specified in ConnectionInfo.json can be connected to, over the port specified for that connector ID in CustomConnectorPortMap.json.

**2. Test connection creation flow** (ValidateAuthentication, ValidateCustomConfiguration, GetDataSourceSchema APIs): This option is to validate the methods specified in ConnectionManagementService. Each of the mentioned methods is invoked and their results are displayed on the console.

**3. Test data source crawl with mocked connection**: This option is to test the methods in ConnectorCrawlerService. The crawl is invoked with the schedule specified in ConnectionInfo.json and the status of the ongoing or last completed crawl gets printed every minute. Once the first crawl finishes successfully, the message that crawl has completed will get displayed, and the platform keeps running to trigger further crawls specified at the interval in ConnectionInfo.json. If incremental crawl frequency is specified in ConnectionInfo.json file, then incremental crawl gets triggered after first full crawl. To stop the platform from crawling, the GraphConnectorAgentTest executable should be closed and restarted. This will enable testing of other options or retesting this option after making any changes to the connector code or to the config files after selecting this option.

![Crawl testing](media/connectors-sdk/testcomplete.png)

## Working of the GraphConnectorAgentTest executable

The ConnectionInfo file is read when the executable is opened. After selecting any of the test options, the platform tries to connect to the connector specified in the ConnectionInfo config file over the port specified for that connector in the CustomConnectorPortMap config file. After successful connection, the platform calls the respective methods pertaining to the test option.

To use test option 2 or 3, the credentials to access the data source has to be specified in the ConnectionInfo.json config. These credentials are read by the platform and passed down to the connector which uses the credentials to access the data source. As long as no external person gets access to the ConnectionInfo.json config file itself, these credentials are secure.
