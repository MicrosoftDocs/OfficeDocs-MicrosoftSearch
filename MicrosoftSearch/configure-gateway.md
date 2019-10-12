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

TODO !!!!!!!!!!!

## Gateway setup
The file share connector relies on PowerBI gateway for connecting with your on-premises file share. Follow the steps to install the gateway:
•	Please visit this link to download and install the latest gateway setup
•	Machine specification requirements are also present in the same page
•	The machine needs to be in the same network as the file share for better performance
•	It is recommended that you use a dedicated machine for this gateway
•	Please use your test tenant credentials to sign in during installation
•	Please add the search admin as the admin for the gateway machine
•	During the private preview and even later, it is recommended that all the regular updates gateway prompts with are installed
•	Please enable gateway monitoring for the private preview using the following steps: 
o	Turn on performance counters and change flags in the configuration file to enable logging. Please follow the steps in this link : https://docs.microsoft.com/en-us/data-integration/gateway/service-gateway-performance
	Please make sure you have access to the logs folder: \Users\PBIEgwService\AppData\Local\Microsoft\On-premises data gateway\Report. If you do not, please change this folder location to one that you have access to. (Use “ReportFilePath” in the config file). 
o	Enable additional logging on the gateway. Turn on the “Additional logging” toggle on the Diagnostics tab of gateway. You can find more information on this here (Update 2).
o	You might be asked to send the logs to the Microsoft team in case of any reported bugs on the gateway.


