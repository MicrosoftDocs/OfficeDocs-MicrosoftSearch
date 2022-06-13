---
title: "Graph connectors SDK Contracts"
ms.author: rchanda
author: rchanda
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
description: "Graph connectors SDK Contracts"
---

# Contracts

The contract protocol buffer files have the following three services which connector developer needs to implement:

## Services

|Services |Description |
|:----------|:-------------|
|ConnectorInfo |Service containing APIs to get information about the connector. If you are using the visual studio extension, this has default implementation and you do not have to make any change. |
|ConnectionManagement |Service containing APIs which are called during the process of custom connector connection creation on M365 admin center. |
|ConnectorCrawl |Service containing APIs which are called during a crawl. |

## APIs

### ConnectorInfo APIs

|Method |Parameters |Return Type |Description |
|:----------|:-------------|:----------|:-------------|
|GetBasicConnectorInfo |GetBasicConnectorInfoRequest |GetBasicConnectorInfoResponse |This API is used to get basic information of the connector. Currently it will be used by the platform to fetch the unique Connector ID. |
|HealthCheck |HealthCheckRequest |HealthCheckResponse |API to check if platform can communicate with the connector server. |

### ConnectorInfo API Models

**GetBasicConnectorInfoResponse**: Response model holding basic connector information

|Property |Type |Description |
|:----------|:-------------|:----------|
|connectorId |String  |Unique identifier for the connector. This should be the unique guid of the connector. |

**GetBasicConnectorInfoRequest**: Request model to retrieve basic connector information. It does not have any properties currently; it will be added in future as required.

**HealthCheckRequest**: Request model for HealthCheck API. It does not have any properties currently, it will be added in future as required.

**HealthCheckResponse**: Response model for HealthCheck API. It does not have any properties currently, it will be added in future as required.

### Connection management APIs

|Method |Parameters |Return Type |Description |
|:----------|:-------------|:----------|:-------------|
|ValidateAuthentication |ValidateAuthenticationRequest |ValidateAuthenticationResponse |This API is called during custom connector connection creation on M365 admin center. The API is used to validate the credentials and data source path provided by the admin in the connection settings step. |
|ValidateCustomConfiguration |ValidateCustomConfigurationRequest |ValidateCustomConfigurationResponse |This API is called during custom connector connection creation on M365 admin center. The API is used to validate the optional configuration provided by the admin in connection configuration step. If no configuration is required for the connector, this API can simply return a success response. |
|GetDataSourceSchema |GetDataSourceSchemaRequest |GetDataSourceSchemaResponse |This API is called during custom connector connection creation on M365 admin center. The API is used to get the data source schema in the format which can be understood by Microsoft Graph. More details are present [here](/graph/api/resources/externalconnectors-schema?view=graph-rest-beta) |

### Connection management API Models

**ValidateAuthenticationRequest**: Request model to validate authentication to data source

|Property |Type |Description |
|:----------|:-------------|:----------|
|authenticationData |AuthenticationData |Holds data source access URL and credential to access it. |

**ValidateAuthenticationResponse**: Response model of validate authentication request to data source

|Property |Type |Description |
|:----------|:-------------|:----------|
|status |OperationStatus |Status of operation and error details in case of error. |

**ValidateCustomConfigurationRequest**: Request model to validate custom configuration information

|Property |Type |Description |
|:----------|:-------------|:----------|
|customConfiguration |CustomConfiguration |Configuration data provided for the connector. |
|authenticationData |AuthenticationData |Holds data source access URL and credential to access it. |

**ValidateCustomConfigurationResponse**: Response model of validation of custom configuration information

|Property |Type |Description |
|:----------|:-------------|:----------|
|status |OperationStatus |Status of operation and error details in case of error. |

**GetDataSourceSchemaRequest**: Request model to get schema information of data source

|Property |Type |Description |
|:----------|:-------------|:----------|
|customConfiguration |CustomConfiguration |Configuration data provided for the connector. |
|authenticationData |AuthenticationData |Holds data source access URL and credential to access it. |

**GetDataSourceSchemaResponse**: Response model of data source schema request

|Property |Type |Description |
|:----------|:-------------|:----------|
|status |OperationStatus |Status of operation and error details in case of error. |
|dataSourceSchema |DataSourceSchema |Data source schema. More details about schema are present [here](/graph/api/resources/externalconnectors-schema?view=graph-rest-beta). |

### Connector Crawler APIs

|Method |Parameters |Return Type |Description |
|:----------|:-------------|:----------|:----------|
|GetCrawlStream |GetCrawlStreamRequest |CrawlStreamBit as a stream |This API is used to read data from the data source. This will be called by platform during crawl. |

### Connector Crawler Models

**GetCrawlStreamRequest**: Request model for getting items during crawl

|Property |Type |Description |
|:----------|:-------------|:----------|
|customConfiguration |CustomConfiguration |Configuration data provided for the connector |
|authenticationData |AuthenticationData |Holds data source access URL and credential to access it |
|crawlProgressMarker |CrawlCheckpoint |Holds data to identify what items were processed the last time crawl ran. This information is returned by the connector along with the items. This can be used by the connector in case of crashes happening on the platform during the crawl. |
|Schema |DataSourceSchema |Schema of connection. This can be used by the connector to identify the property which is content and set it. |

**CrawlStreamBit**: Response model containing the item, status indicating success/failures if any and the indicator/checkpoint for the item being crawled.

|Property |Type |Description |
|:----------|:-------------|:----------|
|status |OperationStatus |Status of operation and error details in case of error |
|crawlItem |CrawlItem |Single item crawled from data source |
|crawlProgressMarker |CrawlCheckpoint |Indicator to identify the item crawled from the data source |

ItemType enum members:

|Member |Value |Description |
|:----------|:-------------|:----------|
|ContentItem |0 |Item with content to ingest. These are the actual data items. Example: website content. |
|LinkItem |1 |Item that acts as a link to a content item. This item info will be used in subsequent crawl to crawl further for that item. Example: Link to website or a folder. |

**CrawlItem**: Represents an entity in the data source. For example: a file, a folder or a record in a table. The max size allowed is 4Mb.

|Property |Type |Description |
|:----------|:-------------|:----------|
|itemType |ItemType |The type of item being sent. This model should have one of contentItem or linkItem set and this enum field should correspond to the item being set – either contentItem or linkItem.
|itemId |string |Unique ID representing the item in the data source |
|contentItem |ContentItem |Item with content to ingest. These are the actual data items. Example: website content. If contentItem is set, linkItem cannot be set. |
|linkItem |LinkItem |Item that acts as a link to a content item. This item info will be used in subsequent crawl to crawl further for that item. Example: Link to website or a folder. If linkItem is set, contentItem cannot be set. |

**ContentItem**: Item that holds the content of the data source entity. This is the with actual content to ingest. Example: website content

|Property |Type |Description |
|:----------|:-------------|:----------|
|propertyValues |SourcePropertyValueMap| Has the key and values of each property in the item |
|accessList |AccessControlList |Access control list to restrict access to the item to specific users/groups |
|content |Content |Content property of the item. The content value can be used when displaying search results. |

**LinkItem**: Item that acts as a link to another item. These link items will be sent again to connector for recrawl. Example: In a folder content, files will be content items and sub folders will be link items.

|Property |Type |Description |
|:----------|:-------------|:----------|
|metadata |map< string, GenericType> |This is a dictionary containing the additional metadata needed by the connector to recrawl the item. |

**AccessControlList**: Holds the access control list which restricts the users to whom the search results are visible.

|Property |Type |Description |
|:----------|:-------------|:----------|
|Entries |repeated AccessControlEntry |List of access control entries. This is of type array or collection. |

AclAccessType enum members:

|Member |Value |Description |
|:----------|:-------------|:----------|
|None |0 |Default value – this is considered as Deny. |
|Grant |1 |Indicates that the entry is for users/groups that have access granted to the item. |
|Deny |2 |Indicates that the entry is for users/groups that have access denied to the item. This overrides Grant for any user/group. |

**AccessControlEntry**: Holds individual access control entries.

|Property |Type |Description |
|:----------|:-------------|:----------|
|accessType |AclAccessType |Access type of the entity – grant or deny |
|principal |Principal |Represents group or user to whom the access is defined |

PrincipalType enum members:

|Member |Value |Description |
|:----------|:-------------|:----------|
|PT_None |0 |Default value. This will be assumed to be User. |
|User |1 |Type of User |
|Group |2 |Type of Group |
|Everyone |3 |Special group to specify access to everyone |
|EveryoneExceptGuests |4 |Special group to specify access to everyone except guests |

IdentitySource enum members:

|Member |Value |Description |
|:----------|:-------------|:----------|
IS_None |0 |Default. This will be assumed to be AAD |
AzureActiveDirectory |1 |Source of identity is AAD |
External |2 |Source of identity is anything other than AAD |

IdentityType enum members:

|Member |Value |Description |
|:----------|:-------------|:----------|
|IT_None |0 |Default. This will be assumed to be AadId |
|ActiveDirectorySId |1 |SID (On premise security identifier) provided by Active Directory (AD) |
|UserPrincipalName |2 |User principal name ([UPN](/azure/active-directory/hybrid/plan-connect-userprincipalname#what-is-userprincipalname))  |
|AadId |3 |Azure Active Directory ID |

**Principal**: Structure to store attributes of the principal (user/group) to whom access is defined.

|Property |Type |Description |
|:----------|:-------------|:----------|
|type |PrincipalType |Type of principal |
|value |string |Principal value – the value of the SID or UPN or AAD id etc |
|identitySource |IdentitySource |Source of identity |
|identityType |IdentityType |Identity representation type |
|identitySourceProperties |map< string, string> |Any additional metadata about the Identity source |

**SourcePropertyValueMap**: Map of source property key and its value as present in the data source. Stores the property values of each item.

|Property |Type |Description |
|:----------|:-------------|:----------|
|values |map< string, GenericType> |Add key and values of the properties of the item. Key will be property name and value will be property value. Example: For a file content – title, modifiedDate etc can be property keys and their values will be the title of the file and file modified date respectively. |

ContentType enum members:

|Member |Value |Description |
|:----------|:-------------|:----------|
|None |0 |Default value |
|Text |1 |Text content type |
|Html |2 |Html content type |
|Binary |3 |Binary content type |
|Bmp |4 |Bmp content type |
|Jpg |5 |Jpg content type |
|Pdf |6 |Pdf content type |
|Png |7 |Png content type |
|Tif |8 |Tif content type |
|UnknownFutureValue |9 |For future-proofing, following MSGraph evolvable enums. All new enums will be added below this one until major API version change. |

**Content**: Value of the content property of the item. This will be used to render search results.

|Property |Type |Description |
|:----------|:-------------|:----------|
|contentType |ContentType |Type of the content |
|contentValue |string |Value of the content property |

**CrawlCheckpoint**: Checkpoint to mark the crawl progress. It is an identifier to mark which item was crawled last. This will be saved by the platform and checkpoint from last successful item batch will be used for resuming crawl in case of failures or crash. The platform will send the checkpoint in GetCrawlStream API.

|Property |Type |Description |
|:----------|:-------------|:----------|
|pagenumber |uint32 |Page number to mark crawl progress |
|batchSize |uint32 |Number of items being returned in every batch. Currently this will be 1 as each item is being streamed individually. |
|customMarkerData |string |Any other custom data needed to identify the last item crawled from the data source. |

**GenericType**: This is a model to hold any of the supported types of values by the platform in certain fields like source property values. Only one of the below fields must be set in this:

|Property |Type |Description |
|:----------|:-------------|:----------|
|stringValue |string |Represents a string value  |
|intValue |int64 |Represents an int64 (long) value |
|doubleValue |double |Represents a double value |
|dateTimeValue |google.protobuf.Timestamp |Represents a dateTime value |
|boolValue |bool |Represents a boolean value |
|stingCollectionValue |StringCollectionType |Represents value which is a collection of strings |
|intCollectionValue |IntCollectionType |Represents value which is a collection of int64 (long) |
|doubleCollectionValue |DoubleCollectionType |Represents value which is a collection of double |
|dateTimeCollectionValue |TimestampCollectionType |Represents value which is a collection of dateTime |

**StringCollectionType**: Collection of string

|Property |Type |Description |
|:----------|:-------------|:----------|
|values |repeated string |Collection or array of strings |

**IntCollectionType**: Collection of int64 (long)

|Property |Type |Description |
|:----------|:-------------|:----------|
|values |repeated int64 |Collection or array of int64 (long) values |

**DoubleCollectionType**: Collection of double

|Property |Type |Description |
|:----------|:-------------|:----------|
|values |repeated double |Collection or array of double values |

**TimestampCollectionType**: Collection of DateTime

|Property |Type |Description |
|:----------|:-------------|:----------|
|values |repeated google.protobuf.Timestamp |Collection or array of dateTime values |

### Common Models

**CustomConfiguration**: Connector specific custom configuration info provided by Search Admin during connection creation. The structure and format of the configuration is not managed by the platform. Connector developers can use format of their choice.

|Property |Type |Description |
|:----------|:-------------|:----------|
|configuration |string |Holds the configuration information as a string. Connector should have the capability to interpret the content of the string. |

AuthenticationType enum members:

|Member |Value |Description |
|:----------|:-------------|:----------|
|Anonymous |0 |No authentication required to access the data source |
|Basic |1 |Basic Authentication in the form of username and password to access the data source |
|Windows |2 |Windows AD based authentication that supports username, password and domain info |

**AuthenticationData**: Holds credential provided by admin to access data source. It contains authentication type, data source url and credentials data.

|Property |Type |Description |
|:----------|:-------------|:----------|
|authType |AuthenticationType |Type of authentication information held in this object |
|DatasourceUrl |string |Url or path to access data source - path to the resource that needs to be crawled. Example: Connection string for a database |
|basicCredential |BasicCredential |Credentials in the form of username and password to access the data source. This will be set exclusive to windowsCredential and the authType will be set to Basic when this is set. |
|windowsCredential |WindowsCredential |Credentials in the form of windows AD username, password and domain to access the data source. This will be set exclusive to basicCredential and the authType will be set to Windows when this is set. |

**BasicCredential**: Represents basic credentials model

|Property |Type |Description |
|:----------|:-------------|:----------|
|username |string |Username for accessing the data source |
|secret |string |Secret to use with username for accessing data source |

**WindowsCredential**: Represents windows credentials model

|Property |Type |Description |
|:----------|:-------------|:----------|
|username |string | Username for accessing the data source |
|secret |string | Secret to use with username for accessing data source |
|domain |string | AD Domain that the account belongs to. If not provided by the admin explicitly, this holds the value of machine name. |

**OperationResult**: Enum containing possible values for the result of operations.

OperationResult enum members:

|Member |Value |Description |
|:----------|:-------------|:----------|
|Success |0 |If operation succeeded without any error |
|PartialSuccess |1 |Operation is a success, but there is a warning message to be processed |
|ValidationFailure |2 |One or more validations failed |
|AuthenticationIssue |3 |Credentials provided did not work |
|DatasourceError |4 |Data source read error |
|NetworkError |5 |Network operation error |
|Cancelled |6 |If operation was cancelled by Cancellation Token |

**OperationStatus**: Represents the status of an operation including error/warnings and retry details. This is part of the response of all APIs in ConnectionManagementService and ConnectorCrawlerService.

|Property |Type |Description |
|:----------|:-------------|:----------|
|result |OperationResult |Result of the operation |
|statusMessage |string |Custom message that can be used for logging and monitoring purposes |
|retryInfo |RetryDetails |Retry information to be used by framework to retry the same operation for a failed operation. Will be ignored in case of success and partial success operations. |

RetryType enum members: This enum is used to define strategy for retrying in case of errors.

|Member |Value |Description |
|:----------|:-------------|:----------|
|NoRetry |0 | No retry has to be made |
|Standard |1 | Standard retry with linear wait time will be made |
|ExponentialBackOff |2 | Retry by exponential backoff will be made |

**RetryDetails**: The is used for communicating the retry policy where retry is required.

|Property |Type |Description |
|:----------|:-------------|:----------|
|type |RetryType |Retry type defines the type of retry strategy required for the error |
|numberOfRetries |uint32 |Number of retries to be done for the exception |
|pauseBetweenRetriesInMilliseconds |uint64 |Gets pause between retries in case of standard retries |
|backoffCoefficient |float |Gets coefficient used in the calculation of Exponential Backoff. |
|backoffRate |float |Gets backoff Rate used in the calculation of Exponential Backoff. |

**DataSourceSchema**: Represents schema of properties that represent a data entity in data source. More details on schema can be found [here](/graph/api/resources/externalconnectors-schema?view=graph-rest-beta)

|Property |Type |Description |
|:----------|:-------------|:----------|
|PropertyList |repeated SourcePropertyDefinition |Represents list of properties that define an item in data source. |

SourcePropertyType enum members:

|Member |Value |Description |
|:----------|:-------------|:----------|
|String |0 |Property of type string |
|Int64 |1 |Property of type int64 (long) |
|Double |2 |Property of type double |
|DateTime |3 |Property of type DateTime |
|Boolean |4 |Property of type Boolean |
|StringCollection |5 |Property of type of array or collection of string type |
|Int64Collection |6 |Property of type of array or collection of long type |
|DoubleCollection |7 |Property of type of array or collection of double type |
|DateTimeCollection |8 |Property of type of array or collection of DateTime type |
|CollectionOfString |9 |Property of type of array or collection of string type |
|CollectionOfInt64 |10 |Property of type of array or collection of long type |
|CollectionOfDouble |11 |Property of type of array or collection of double type |
|CollectionOfDateTime |12 |Property of type of array or collection of DateTime type |

SearchAnnotations enum members:

|Member |Value |Description |
|:----------|:-------------|:----------|
|None |0 |None |
|IsSearchable |1 |If a property is searchable, its value is added to the full text index. When a user performs a search, we return results if there is a search hit in one of the searchable fields or its content. Eg., If property is "Author", searching "Smith" returns items whose Author property contains "Smith". |
|IsQueryable |2 |If a property is queryable, you can query against it using knowledge query language (KQL). KQL consists of 1 or more free text keywords (words or phrases) or property restrictions. The property name must be included in the query, either specified in the query itself or included in the query programmatically. You can use prefix matching with the wildcard operator(\*) Eg., If property is "Author", search query can be "Author: Smith" |
|IsRetrievable |4 |If a property is retrievable, its value can be returned in search results. Any property that you want to add in the display template or be returned from the query and be relevant in search results must be retrievable. Marking large or too many properties as retrievable will increase search latency. Be selective and choose relevant properties. |
|IsContent |8 |Content property is to identify a property that can be full text indexed. Admins will choose among the available properties as to which should be the property to be treated as content for that specific connection. More on the content property [here](/graph/connecting-external-content-manage-items#content) |
|IsRefinable |16 |If a property is refinable, an admin can configure it as a custom filter in the Microsoft Search results page. A refinable property cannot be searchable. |

**SearchPropertyLabel**: These are well-known tags published by Microsoft that you can add against a property in your schema. Adding a semantic label helps various Microsoft products understand the property and provide a better experience. Read more [here](/graph/connecting-external-content-manage-schema#semantic-labels)

SearchPropertyLabel enum members:

|Member |Value |Description |
|:----------|:-------------|:----------|
|Title |0 |The title of the item that you want shown in search and other experiences. |
|Url |1 |The target URL of the item in the data source. |
|CreatedBy |2 |Name of the person who created the item in the data source. |
|LastModifiedBy |3 |Name of the person who most recently edited the item in the data source. |
|Authors |4 |Name of all the people who participated/collaborated on the item in the data source. |
|CreatedDateTime |5 |Date and time that the item was created in the data source. |
|LastModifiedDateTime |6 |Date and time the item was last modified in the data source. |
|FileName |7 |In case of a file, the name of the file in the data source. |
|FileExtension |8 |In case of a file, the extension of the file in the data source . |
|LastModifiedByUpn |9 |[UPN](/azure/active-directory/hybrid/plan-connect-userprincipalname#what-is-userprincipalname) of the person who most recently edited the item in the data source. |
|CreatedByUpn |10 |[UPN](/azure/active-directory/hybrid/plan-connect-userprincipalname#what-is-userprincipalname) of the person who created the item in the data source. |
|AuthorsUpn |11 |[UPNs](/azure/active-directory/hybrid/plan-connect-userprincipalname#what-is-userprincipalname) of all the people who participated/collaborated on the item in the data source. |
|UnknownFutureValue |12 |For future-proofing, following MSGraph evolvable enums.All new enums should be added below this one until major API version change. |
|ContainerName |13 |Name of the container. |
|ContainerUrl |14 | The URL of the container. |
|IconUrl | 15 |The URL of an icon. |

**SourcePropertyDefinition**: Defines a single source property for an item in data source. Read more about schema property definitions [here](/graph/api/resources/externalconnectors-property?view=graph-rest-1.0)

|Property |Type |Description |
|:----------|:-------------|:----------|
|name |string | Name of the property |
|type |SourcePropertyType | Data type of the property |
|defaultSearchAnnotations |uint32 | Default search annotations for the property |
|requiredSearchAnnotations |uint32 | Required search annotations.Certain properties like "id" is always set isQueryable true and isRetrievable true. |
|defaultSemanticLabels |repeated SearchPropertyLabel | List of semantic labels for the source property |
|order |int32 |\[Optional\]Order of this source property. Used by UI for sorting the search results. |
|label |string |\[Optional\]Label of this source property. Used by search results UI to display the label (human readable name). |
|aliases |repeated string |\[Optional\]List of aliases of this source property. |
