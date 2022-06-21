---
title: "Graph connectors SDK Contracts Connector Crawler API"
ms.author: rchanda
author: rchanda
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
description: "Graph connectors SDK Contracts Connector Crawler API"
---

## Connector Crawler APIs and Models

These APIs are called during a crawl

### Connector Crawler APIs

|Method |Parameters |Return Type |Description |
|:----------|:-------------|:----------|:----------|
|GetCrawlStream |GetCrawlStreamRequest |CrawlStreamBit as a stream |This API is used to read data from the data source. This will be called by platform during during full and periodic full crawls where all items should be read from the datasource and returned to the platform. |
|GetIncrementalCrawlStream |GetIncrementalCrawlStreamRequest |IncrementalCrawlStreamBit as a stream |This API is used to read data from the data source. This will be called by platform during incremental crawls where only the incremental changes in items since last incremental crawl needs to be returned to the platform. This is optional to implement. |

### Connector Crawler Models

#### GetCrawlStreamRequest

Request model for getting items during crawl

|Property |Type |Description |
|:----------|:-------------|:----------|
|customConfiguration |CustomConfiguration |Configuration data provided for the connector |
|authenticationData |AuthenticationData |Holds data source access URL and credential to access it |
|crawlProgressMarker |CrawlCheckpoint |Holds data to identify what items were processed the last time crawl ran. This information is returned by the connector along with the items. This can be used by the connector in case of crashes happening on the platform during the crawl. |
|Schema |DataSourceSchema |Schema of connection. This can be used by the connector to identify the property which is content and set it. |

#### CrawlStreamBit

Response model containing the item, status indicating success/failures if any and the indicator/checkpoint for the item being crawled during full/periodic full crawl.

|Property |Type |Description |
|:----------|:-------------|:----------|
|status |OperationStatus |Status of operation and error details in case of error |
|crawlItem |CrawlItem |Single item crawled from data source |
|crawlProgressMarker |CrawlCheckpoint |Indicator to identify the item crawled from the data source |

#### GetIncrementalCrawlStreamRequest

Request model for getting items during incremental crawl.

|Property |Type |Description |
|:----------|:-------------|:----------|
|customConfiguration |CustomConfiguration |Configuration data provided for the connector |
|authenticationData |AuthenticationData |Holds data source access URL and credential to access it |
|crawlProgressMarker |CrawlCheckpoint |Holds data to identify what items were processed the last time crawl ran. This information is returned by the connector along with the items. This can be used by the connector in case of crashes happening on the platform during the crawl. |
|schema |DataSourceSchema |Schema of connection. This can be used by the connector to identify the property which is content and set it. |
|previousCrawlStartTimeInUtc |Timestamp |DateTime value of previous crawl start time in UTC. This value can be used in first incremental crawl. For subsequent calls checkpoint value should be used. |

#### IncrementalCrawlStreamBit

Response model containing the item, status indicating success/failures if any and the indicator/checkpoint for the item being crawled during incremental crawl.

|Property |Type |Description |
|:----------|:-------------|:----------|
|status |OperationStatus |Status of operation and error details in case of error |
|crawlItem |IncrementalCrawlItem |Single item crawled from datasource during incremental crawl |
|crawlProgressMarker |CrawlCheckpoint |Indicator to identify the last item crawled from the datasource during last incremental crawl |

ItemType enum members for CrawlItem:

|Member |Value |Description |
|:----------|:-------------|:----------|
|ContentItem |0 |Item with content to ingest. These are the actual data items. Example: website content. |
|LinkItem |1 |Item that acts as a link to a content item. This item info will be used in subsequent crawl to crawl further for that item. Example: Link to website or a folder. |

#### CrawlItem

Represents an entity in the data source. For example: a file, a folder or a record in a table. The max size allowed is 4Mb.

|Property |Type |Description |
|:----------|:-------------|:----------|
|itemType |ItemType |The type of item being sent. This model should have one of contentItem or linkItem set and this enum field should correspond to the item being set – either contentItem or linkItem.
|itemId |string |Unique ID representing the item in the data source |
|contentItem |ContentItem |Item with content to ingest. These are the actual data items. Example: website content. If contentItem is set, linkItem cannot be set. |
|linkItem |LinkItem |Item that acts as a link to a content item. This item info will be used in subsequent crawl to crawl further for that item. Example: Link to website or a folder. If linkItem is set, contentItem cannot be set. |

ItemType enum members for IncrementalCrawlItem:

|Member |Value |Description |
|:----------|:-------------|:----------|
|ContentItem |0 |Item with content to ingest. These are the actual data items. Example: website content |
|LinkItem |1 |Item that acts as a link to a content item. This item info will be used in subsequent crawl to crawl further for that item. Example: Link to website or a folder. |
|DeletedItem |2 |Item that is deleted from datasource and should be deleted from index. |

#### IncrementalCrawlItem

Represents an entity in the data source. For example: a file, a folder or a record in a table. The max size allowed is 4Mb.

|Property |Type |Description |
|:----------|:-------------|:----------|
|itemType |ItemType |The type of item being sent. This model should have one of contentItem or linkItem or deletedItem set and this enum field should correspond to the item being set – either contentItem or linkItem or deletedItem. |
|itemId |string |Unique ID representing the item in the data source |
|contentItem |ContentItem |Item with content to ingest. These are the actual data items. Example website content. If contentItem is set, linkItem or deletedItem cannot be set. |
|linkItem |LinkItem |Item that acts as a link to a content item. This item info will be used in subsequent crawl to crawl further for that item. Example: Link to website or a folder. If linkItem is set, contentItem or deletedItem cannot be set. |
|deletedItem |DeletedItem |Item that is deleted from the datasource and should be removed from the index. If deletedItem is set, contentItem or linkItem cannot be set. |

#### ContentItem

Item that holds the content of the data source entity. This is the with actual content to ingest. Example: website content

|Property |Type |Description |
|:----------|:-------------|:----------|
|propertyValues |SourcePropertyValueMap| Has the key and values of each property in the item |
|accessList |AccessControlList |Access control list to restrict access to the item to specific users/groups |
|content |Content |Content property of the item. The content value can be used when displaying search results. |

#### LinkItem

Item that acts as a link to another item. These link items will be sent again to connector for recrawl. Example: In a folder content, files will be content items and sub folders will be link items.

|Property |Type |Description |
|:----------|:-------------|:----------|
|metadata |map< string, GenericType> |This is a dictionary containing the additional metadata needed by the connector to recrawl the item. |

#### DeletedItem

Represents an item that is deleted from the datasource and has to be removed from the index.

#### AccessControlList

Holds the access control list which restricts the users to whom the search results are visible.

|Property |Type |Description |
|:----------|:-------------|:----------|
|Entries |repeated AccessControlEntry |List of access control entries. This is of type array or collection. |

AclAccessType enum members:

|Member |Value |Description |
|:----------|:-------------|:----------|
|None |0 |Default value – this is considered as Deny. |
|Grant |1 |Indicates that the entry is for users/groups that have access granted to the item. |
|Deny |2 |Indicates that the entry is for users/groups that have access denied to the item. This overrides Grant for any user/group. |

#### AccessControlEntry

Holds individual access control entries.

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

#### Principal

Structure to store attributes of the principal (user/group) to whom access is defined.

|Property |Type |Description |
|:----------|:-------------|:----------|
|type |PrincipalType |Type of principal |
|value |string |Principal value – the value of the SID or UPN or AAD id etc |
|identitySource |IdentitySource |Source of identity |
|identityType |IdentityType |Identity representation type |
|identitySourceProperties |map< string, string> |Any additional metadata about the Identity source |

#### SourcePropertyValueMap

Map of source property key and its value as present in the data source. Stores the property values of each item.

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

#### Content

Value of the content property of the item. This will be used to render search results.

|Property |Type |Description |
|:----------|:-------------|:----------|
|contentType |ContentType |Type of the content |
|contentValue |string |Value of the content property |

#### CrawlCheckpoint

Checkpoint to mark the crawl progress. It is an identifier to mark which item was crawled last. This will be saved by the platform and checkpoint from last successful item batch will be used for resuming crawl in case of failures or crash. The platform will send the checkpoint in GetCrawlStream API.

|Property |Type |Description |
|:----------|:-------------|:----------|
|pagenumber |uint32 |Page number to mark crawl progress |
|batchSize |uint32 |Number of items being returned in every batch. Currently this will be 1 as each item is being streamed individually. |
|customMarkerData |string |Any other custom data needed to identify the last item crawled from the data source. |

#### GenericType

This is a model to hold any of the supported types of values by the platform in certain fields like source property values. Only one of the below fields must be set in this:

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

#### StringCollectionType

Collection of string

|Property |Type |Description |
|:----------|:-------------|:----------|
|values |repeated string |Collection or array of strings |

#### IntCollectionType

Collection of int64 (long)

|Property |Type |Description |
|:----------|:-------------|:----------|
|values |repeated int64 |Collection or array of int64 (long) values |

#### DoubleCollectionType

Collection of double

|Property |Type |Description |
|:----------|:-------------|:----------|
|values |repeated double |Collection or array of double values |

#### TimestampCollectionType

Collection of DateTime

|Property |Type |Description |
|:----------|:-------------|:----------|
|values |repeated google.protobuf.Timestamp |Collection or array of dateTime values |
