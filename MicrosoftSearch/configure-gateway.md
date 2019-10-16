---
title: "Configure a gateway connection"
ms.author: v-pamcn
author: TrishaMc1
manager: mnirkhe
ms.date: 10/08/2019
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Priority
search.appverid:
- BFB160
- MET150
- MOE150
description: "Configure a gateway connection"
---

# Configure a gateway connection
The on-premises data gateway acts as a bridge to provide quick and secure data transfer between on-premises data (data that isn't in the cloud) and several Microsoft cloud services, such as Power BI. By using a gateway, organizations can keep databases and other data sources on their on-premises networks, yet securely use that on-premises data in cloud services.

## Installing your gateway
You can follow the steps in [this article](https://docs.microsoft.com/en-us/data-integration/gateway/service-gateway-install) to download and install your Power BI gateway.

Please note the following machine specification requirements for configuration:
* The machine needs to be in the same network as the on-premises database for better performance 
* It is recommended you use a dedicated machine for this gateway

## Things to note during setup
* Use your test tenant credentials to sign in during installation
* Add the search admin as the admin for the gateway machine
* Ensure all regular updates the gateway prompts are installed

## Enabling gateway monitoring 
Turn on performance counters and change flags in the configuration file to enable logging by following [these steps](https://docs.microsoft.com/en-us/data-integration/gateway/service-gateway-performance).

>[!NOTE]
Make sure you have access to the logs folder: *\Users\PBIEgwService\AppData\Local\Microsoft\On-premises data gateway\Report* <br></br> If you do not, please change this folder location to one that you have access to. (Use “ReportFilePath” in the config file). Turn on the “Additional logging” toggle on the Diagnostics tab of gateway to enable additional logging.

>[!NOTE]
You might be asked to send the logs to the Microsoft team in case of any reported bugs on the gateway.

For additional resources on configuring your gateway connection see [this in-depth article on on-premises data gateways](https://docs.microsoft.com/en-us/power-bi/service-gateway-onprem-indepth).


