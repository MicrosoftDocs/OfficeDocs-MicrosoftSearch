---
title: "Graph connectors SDK best practices"
ms.author: rchanda
author: rchanda
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
description: "Graph connectors SDK best practices"
---

# Graph connectors SDK Best practices

The following section contains the best practices to follow while implementing a custom connector using the Graph connectors SDK

## Using crawl progress marker

The crawl progress marker acts as an identifier for the particular item sent by the connector that was last processed by the connector platform. There are two types of crawls which happen: Periodic full and incremental crawls.

Periodic full crawls are meant to get all items in the data source. The items which are modified nor not present in the index  are only ingested and items not found in data source are deleted from the index.

Incremental crawls are meant for only getting items added/modified since the last incremental crawl. The connector can send items to be deleted as well as a part of this. For the first incremental crawl, the start time of last full crawl is sent as well. The connector can optionally use this to fetch items changed only after that.

Both these crawls have their own crawl progress markers.

### Usage of crawl progress marker during periodic full crawls

For periodic full crawls, the crawl progress marker is sent only in case the previous crawl crashed or if the Graph connector agent was offline for a period of time causing a scheduled crawl to be missed. In case of scheduled crawl without any previous crawl crashes, the crawl progress marker is not sent. In these cases, the data source has to be crawled from the beginning.

### Usage of crawl progress marker during incremental crawls

For incremental crawls, the crawl progress marker sent by the connector to the connector platform during the previous incremental crawl is sent to the connector. This can be used by the connector to fetch the items added or modified after this marker.

## Constructing generic types

The property values of the content item can have a range of data types. Since gRPC does not have a construct for generic objects, we have created a [GenericType](/microsoftsearch/custom-connector-sdk-contracts-connectorcrawler#generictype) structure that can hold any of the supported data types. GenericType has the following structure:

```csharp
// Represents a generic type that can hold any supported value
message GenericType {
 // Value of the Generic type
 oneof value {
  // String type value
  string stringValue = 1;

  // Long value
  int64 intValue = 2;


  // Double value
  double doubleValue = 3;

  // DateTime value
  google.protobuf.Timestamp dateTimeValue = 4;

  // Boolean value
  bool boolValue = 5;

  // String collection value
  StringCollectionType stringCollectionValue = 6;

  // Long collection value
  IntCollectionType intCollectionValue = 7;

  // Double collection value
  DoubleCollectionType doubleCollectionValue = 8;

  // DateTime collection value
  TimestampCollectionType dateTimeCollectionValue = 9;
 }
}

// Collection of string
message StringCollectionType {
 // Value of string collection
 repeated string values = 1;
}

// Collection of long
message IntCollectionType {
 // Value of long collection
 repeated int64 values = 1;
}

// Collection of double
message DoubleCollectionType {
 // Value of double collection
 repeated double values = 1;
}

// Collection of DateTime
message TimestampCollectionType {
 // Value of DateTime collection
 repeated google.protobuf.Timestamp values = 1;
}

```

GenericType can have one of the types of string/int64/double/DateTime/Boolean or a collection of string/int64/double/DateTime. Some samples to set these types:

```csharp
// Setting string value in generic type
    GenericType stringType = new GenericType
    {
        StringValue = "Hello"
    };

    // Setting int64 value in generic type
    GenericType int64Type = new GenericType
    {
        IntValue = 1000
    };

    // Setting double value in generic type
    GenericType doubleType = new GenericType
    {
        DoubleValue = 12.54
    };

    // Setting dateTime value in generic type
    GenericType dateTimeType = new GenericType
    {
        DateTimeValue = Google.Protobuf.WellKnownTypes.Timestamp.FromDateTime(DateTime.UtcNow)
    };

    // Setting boolean value in generic type
    GenericType boolType = new GenericType
    {
        BoolValue = true
    };

    // Setting string collection value in generic type - Initialize the string collection first, add the values to the string collection and then set it in the generic type
    StringCollectionType stringCollection = new StringCollectionType();
    stringCollection.Values.Add("Value1");
    stringCollection.Values.Add("Value2");
    GenericType stringCollectionType = new GenericType
    {
        StringCollectionValue = stringCollection
    };

    // Setting int64 collection value in generic type - Initialize the int64 collection first, add the values to the int64 collection and then set it in the generic type
    IntCollectionType intCollection = new IntCollectionType();
    intCollection.Values.Add(1234);
    intCollection.Values.Add(5436);
    GenericType intCollectionType = new GenericType
    {
        IntCollectionValue = intCollection
    };

    // Setting double collection value in generic type - Initialize the double collection first, add the values to the double collection and then set it in the generic type
    DoubleCollectionType doubleCollection = new DoubleCollectionType();
    doubleCollection.Values.Add(12.54);
    doubleCollection.Values.Add(34.213);
    GenericType doubleCollectionType = new GenericType
    {
        DoubleCollectionValue = doubleCollection
    };

    // Setting datetime collection value in generic type - Initialize the datetime collection first, add the values to the datetime collection and then set it in the generic type
    TimestampCollectionType dateTimeCollection = new TimestampCollectionType();
    dateTimeCollection.Values.Add(Google.Protobuf.WellKnownTypes.Timestamp.FromDateTime(DateTime.UtcNow));
    dateTimeCollection.Values.Add(Google.Protobuf.WellKnownTypes.Timestamp.FromDateTime(DateTime.UtcNow.AddDays(-1)));
    GenericType dateTimeCollectionType = new GenericType
    {
        DateTimeCollectionValue = dateTimeCollection
    };

```

## Building search schema

Schema has certain restrictions as listed below:

**Property name**: The name of the property can have a maximum of 32 characters. Only alphanumeric characters are allowed. For example, each string may not contain control characters, whitespace, or any of the following: :, ;, ,, (, ), [, ], {, }, %, $, +, !, *, =, &, ?, @, #, \\, ~, ', ", <, >, `, ^.

**Search annotations**: Following are the set of rules to follow for search annotations:

   • Only properties of type String or StringCollection can be searchable.

   • Only properties of type String can be a content property.

   • Content properties must be searchable.

   • Content properties cannot be queryable or retrievable.

   • Refinable property should not be searchable.

   • Refinable property should be queryable and retrievable.

   • Boolean properties cannot be refinable.

**Aliases**: A set of aliases or a friendly name for the property. Maximum 32 characters. Only alphanumeric characters allowed. For example, each string may not contain control characters, whitespace, or any of the following: :, ;, ,, (, ), [, ], {, }, %, $, +, !, *, =, &, ?, @, #, \\, ~, ', ", <, >, `, ^.

## Fetching items during crawl

The GetCrawlStream method is a [server streaming method](https://grpc.io/docs/what-is-grpc/core-concepts/#server-streaming-rpc). Each item crawled from the datasource is converted into a [CrawlStreamBit](/microsoftsearch/custom-connector-sdk-contracts-connectorcrawler#crawlstreambit) and sent over the response stream. To get a good throughput, it is best if the connector retrieves a batch of items from the data source and converts each item to the CrawlStreamBit and sends them over the response stream. The batch size depends on the datasource, we recommend 25 as an optimal batch size to maintain continuous flow of items over the stream.

## Exception handling in connector code
  
All responses from the gRPC calls have an [OperationStatus](/microsoftsearch/custom-connector-sdk-contracts-common#operationstatus) which indicates if the operation succeeded or failed and the failure reason and retry details in case of failures. We recommend that all code should be wrapped in a try-catch block and all exceptions be logged by the connector and a proper operation status be sent to the platform. In the case of connection management flows, the StatusMessage that is sent as part of the response is displayed in the M365 Admin Center. So, sending meaningful messages will be helpful for debugging errors on the connector. Unhandled exceptions will result in Unknown or generic error messages on the UI, which won’t be helpful in debugging.

## Timeouts

All methods in [ConnectionManagementService](/MicrosoftSearch/custom-connector-sdk-contracts-connectionmanagement) should complete and return within 30 seconds, otherwise the platform will timeout the requests.

## Sending back errors from connector to platform

All responses have the [OperationStatus](/microsoftsearch/custom-connector-sdk-contracts-common#operationstatus) set in the response structure. In case of any errors, connectors are expected to use this OperationStatus to send the failure reason and retry information back to platform. It is recommended to use this to set the errors during crawls in case of connection level errors like expired credentials to access datasource.
OperationStatus structure has 3 fields that can be used to represent any errors:

### OperationResult

This is an enum that can hold the failure reason.

### StatusMessage

This is a custom message to show the failure reason. This message will be displayed to admins during connection setup. For example if the provided credentials are incorrect during ValidateAuthentication, the OperationStatus can be set to AuthenticationIssue and statusMessage can be set to “Incorrect credentials provided.”. During ValidateAuthentication this statusMessage will be shown to the search admin and during crawls this will move the connection to failed state and display the authentication error to the admin and prompt the admin to update the credentials to access the datasource.

### RetryDetails

In case of transient and retriable errors that occur during crawls, the retry details can be sent for the platform to retry. The retry can be standard or exponential backoff and the pause time, backoff rate and backoff coefficient can be set by the connector and sent back. For example, if the datasource is throttled during the crawl, the connector can set the OperationResult to DatasourceError and send the retry details according to the retry-header in the response headers from datasource.

## Error mapping for OperationResult

The following errors move the connection to failed state:

* OperationResult.AuthenticationIssue

* OperationResult.ValidationFailure

The other operation codes will be treated as transient failures and will be retried in subsequent crawls.
