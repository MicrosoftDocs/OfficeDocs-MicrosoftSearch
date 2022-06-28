---
title: "Graph connectors SDK Troubleshooting"
ms.author: rchanda
author: rchanda
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
description: "Graph connectors SDK Troubleshooting"
---

# Graph connectors SDK Troubleshooting

The following section explains some of the most common issues faced and how to troubleshoot them.

## Troubleshooting items missing from index

If items present previously are missing from the index, it could be due to the delete detection logic in the platform. When the connector sends success response in [OperationStatus](/microsoftsearch/custom-connector-sdk-contracts-common#operationstatus), the items missing from the connector response, but already present in index, are considered to be deleted and will be removed from the index. In case the connector sends transient failure responses as well, if more than 10% of the items have resulted in crawl failures, the items that aren't seen in the last 2 crawls will get deleted.

## Updating port mapping configuration file

When the connector needs to be run on a different port, the port map config file has to be updated with the new values. Whenever port map config file is edited the GCA service must be restarted for the changes to take effect. To restart this, open services.msc and restart GcaHostService:

![Services window](media/connectors-sdk/services.png)

## Troubleshooting connector service unavailability

If the crawls are failing with connector unavailable on specified port, check the following scenarios:  

1. The connector is indeed running on the specified port and hasn't crashed or got stuck.

2. The port specified in the port map configuration file is correct.

3. If the port map configuration file has been edited, make sure that the GcaHostService was restarted as mentioned in [Updating port mapping configuration](#updating-port-mapping-configuration-file).

## Handling RPC errors

If you see any RPC errors during the communication between the Graph connector Agent platform and the connector, check [this](https://grpc.github.io/grpc/core/md_doc_statuscodes.html) page to see the explanation of RPC error codes.

If the error code is Unknown, the most likely reason is that there's some unhandled exception in your connector code. Make sure there's no unhandled exception and that a proper response is sent with success/failure operation status in all cases.
