---
title: "Graph connectors SDK Contracts Common Models"
ms.author: rchanda
author: rchanda
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
description: "Graph connectors SDK Contracts Common Models"
---

# Common Models

## CustomConfiguration

Connector specific custom configuration info provided by Search Admin during connection creation. The structure and format of the configuration is not managed by the platform. Connector developers can use format of their choice.

|Property |Type |Description |
|:----------|:-------------|:----------|
|configuration |string |Holds the configuration information as a string. Connector should have the capability to interpret the content of the string. |

## AuthenticationType enum members

|Member |Value |Description |
|:----------|:-------------|:----------|
|Anonymous |0 |No authentication required to access the data source |
|Basic |1 |Basic Authentication in the form of username and password to access the data source |
|Windows |2 |Windows AD based authentication that supports username, password and domain info |
|oAuth2ClientCredential |3 |OAuth2 based authentication with client credentials - supports app id and app secret |

## AuthenticationData

Holds credential provided by admin to access data source. It contains authentication type, data source url and credentials data.

|Property |Type |Description |
|:----------|:-------------|:----------|
|authType |[AuthenticationType](#authenticationtype-enum-members) |Type of authentication information held in this object |
|DatasourceUrl |string |Url or path to access data source - path to the resource that needs to be crawled. Example: Connection string for a database |
|basicCredential |[BasicCredential](#basiccredential) |Credentials in the form of username and password to access the data source. This will be set exclusive to windowsCredential and the authType will be set to Basic when this is set. |
|windowsCredential |[WindowsCredential](#windowscredential) |Credentials in the form of windows AD username, password and domain to access the data source. This will be set exclusive to basicCredential and the authType will be set to Windows when this is set. |
|oAuth2ClientCredential |[oAuth2ClientCredential](#oauth2clientcredential) |Credentials in the form of app id and app secret for OAuth client credentials based authentication for accessing the datasource. This will be set exclusive to oAuth2ClientCredential and the authType will be set to oAuth2ClientCredential when this is set. |

## BasicCredential

Represents basic credentials model

|Property |Type |Description |
|:----------|:-------------|:----------|
|username |string |Username for accessing the data source |
|secret |string |Secret to use with username for accessing data source |

## WindowsCredential

Represents windows credentials model

|Property |Type |Description |
|:----------|:-------------|:----------|
|username |string | Username for accessing the data source |
|secret |string | Secret to use with username for accessing data source |
|domain |string | AD Domain that the account belongs to. If not provided by the admin explicitly, this holds the value of machine name. |

## oAuth2ClientCredential

Represents credential model for oauth2 client credentials

|Property |Type |Description |
|:----------|:-------------|:----------|
|appId |string |Application id/client id for the OAuth2 application |
|appSecret |String |Application secret/client secret for the OAuth2 application |
|oAuth2ClientCredentialResponse |[oAuth2ClientCredentialResponse](#oauth2clientcredentialresponse) |Contains OAuth token related details. This will be set to the response which connector sends after the first validate authentication call succeeds. |

## oAuth2ClientCredentialResponse

Represents response model from auth server for OAuth2 token request. The fields present in this model are the common response fields specified in OAuth2 documentation. Additionally idToken can be set when OpenIDConnect is supported by the auth servers.

|Property |Type |Description |
|:----------|:-------------|:----------|
|accessToken |string |The access token from auth server |
|refreshToken |string |The refresh token if auth server sends it |
tokenType |string |Type of the token – usually Bearer token for OAuth |
expiresIn |uint64 |The expiry time of the token in unix timestamp |
scope |string |Scopes supported by the token if auth server sends it |
idToken |string  |The id token if auth server supports open ID connect |

## OperationResult

Enum containing possible values for the result of operations.

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
|TokenExpired |7 |To be used in OAuth flow when the token sent to the connector by the platform has expired. During crawl, on receiving this status, the platform will trigger the refresh token flow and call RefreshAccessToken method in ConnectorOAuthService. |

## OperationStatus

Represents the status of an operation including error/warnings and retry details. This is part of the response of all APIs in ConnectionManagementService and ConnectorCrawlerService.

|Property |Type |Description |
|:----------|:-------------|:----------|
|result |[OperationResult](#operationresult) |Result of the operation |
|statusMessage |string |Custom message that can be used for logging and monitoring purposes |
|retryInfo |[RetryDetails](#retrydetails) |Retry information to be used by framework to retry the same operation for a failed operation. Will be ignored in case of success and partial success operations. |

## RetryType enum members

This enum is used to define strategy for retrying in case of errors.

|Member |Value |Description |
|:----------|:-------------|:----------|
|NoRetry |0 | No retry has to be made |
|Standard |1 | Standard retry with linear wait time will be made |
|ExponentialBackOff |2 | Retry by exponential backoff will be made |

## RetryDetails

This is used for communicating the retry policy where retry is required.

|Property |Type |Description |
|:----------|:-------------|:----------|
|type |[RetryType](#retrytype-enum-members) |Retry type defines the type of retry strategy required for the error |
|numberOfRetries |uint32 |Number of retries to be done for the exception |
|pauseBetweenRetriesInMilliseconds |uint64 |Gets pause between retries in case of standard retries |
|backoffCoefficient |float |Gets coefficient used in the calculation of Exponential Backoff. |
|backoffRate |float |Gets backoff Rate used in the calculation of Exponential Backoff. |

## DataSourceSchema

Represents schema of properties that represent a data entity in data source. More details on schema can be found [here](/graph/api/resources/externalconnectors-schema?view=graph-rest-beta)

|Property |Type |Description |
|:----------|:-------------|:----------|
|PropertyList |repeated [SourcePropertyDefinition](#sourcepropertydefinition) |Represents list of properties that define an item in data source. |

## SourcePropertyType enum members

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

## SearchAnnotations enum members

|Member |Value |Description |
|:----------|:-------------|:----------|
|None |0 |None |
|IsSearchable |1 |If a property is searchable, its value is added to the full text index. When a user performs a search, we return results if there is a search hit in one of the searchable fields or its content. Eg., If property is "Author", searching "Smith" returns items whose Author property contains "Smith". |
|IsQueryable |2 |If a property is queryable, you can query against it using knowledge query language (KQL). KQL consists of 1 or more free text keywords (words or phrases) or property restrictions. The property name must be included in the query, either specified in the query itself or included in the query programmatically. You can use prefix matching with the wildcard operator(\*) Eg., If property is "Author", search query can be "Author: Smith" |
|IsRetrievable |4 |If a property is retrievable, its value can be returned in search results. Any property that you want to add in the display template or be returned from the query and be relevant in search results must be retrievable. Marking large or too many properties as retrievable will increase search latency. Be selective and choose relevant properties. |
|IsContent |8 |Content property is to identify a property that can be full text indexed. Admins will choose among the available properties as to which should be the property to be treated as content for that specific connection. More on the content property [here](/graph/connecting-external-content-manage-items#content) |
|IsRefinable |16 |If a property is refinable, an admin can configure it as a custom filter in the Microsoft Search results page. A refinable property cannot be searchable. |

## SearchPropertyLabel

These are well-known tags published by Microsoft that you can add against a property in your schema. Adding a semantic label helps various Microsoft products understand the property and provide a better experience. Read more [here](/graph/connecting-external-content-manage-schema#semantic-labels)

### SearchPropertyLabel enum members

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

## SourcePropertyDefinition

Defines a single source property for an item in data source. Read more about schema property definitions [here](/graph/api/resources/externalconnectors-property?view=graph-rest-1.0)

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
