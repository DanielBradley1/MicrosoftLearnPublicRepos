<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-31 -->

# discoveredCloudAppDetail resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details about a discovered cloud app.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-discoveredcloudappdetail-get?view=graph-rest-beta) | [microsoft.graph.security.discoveredCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta) | Get an overview of the [usage of discovered cloud apps](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta). |
| [Get discovered cloud app info](https://learn.microsoft.com/en-us/graph/api/security-discoveredcloudappinfo-get?view=graph-rest-beta) | [microsoft.graph.security.discoveredCloudAppInfo](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappinfo?view=graph-rest-beta) | Get the [details](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappinfo?view=graph-rest-beta) of the security, legal, and compliance risk attributes of the discovered cloud apps. |
| [List IP addresses](https://learn.microsoft.com/en-us/graph/api/security-discoveredcloudappdetail-list-ipaddresses?view=graph-rest-beta) | [microsoft.graph.security.discoveredCloudAppIPAddress](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappipaddress?view=graph-rest-beta) collection | Get the list of [IP addresses](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappipaddress?view=graph-rest-beta) associated with a discovered cloud app. |
| [List users](https://learn.microsoft.com/en-us/graph/api/security-discoveredcloudappdetail-list-users?view=graph-rest-beta) | [microsoft.graph.security.discoveredCloudAppUser](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappuser?view=graph-rest-beta) collection | Get a list of [users](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappuser?view=graph-rest-beta) who accessed a discovered cloud app. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| category | [microsoft.graph.security.appCategory](https://learn.microsoft.com/en-us/graph/api/resources/security-appcategory?view=graph-rest-beta) | The category of the discovered app. |
| displayName | String | The app name. |
| domains | String collection | The domain. |
| downloadNetworkTrafficInBytes | Int64 | The download traffic size. |
| id | String | The SaaSDB ID of the app. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| ipAddressCount | Int64 | The IP address. |
| lastSeenDateTime | DateTimeOffset | The last seen date of the discovered app. The Timestamp represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| riskScore | Int64 | The risk score of the app. |
| tags | String collection | The tags applied to an app. Possible values include `Unsanctioned`, `Sanctioned`, `Monitored`, or a custom value. |
| transactionCount | Int64 | The app transaction count. |
| uploadNetworkTrafficInBytes | Int64 | The app upload traffic size, in bytes. |
| userCount | Int64 | The count of users who use the app. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appInfo | [microsoft.graph.security.discoveredCloudAppInfo](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappinfo?view=graph-rest-beta) | The application information. |
| ipAddresses | [microsoft.graph.security.discoveredCloudAppIPAddress](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappipaddress?view=graph-rest-beta) collection | The list of IP addresses accessed by the app. |
| users | [microsoft.graph.security.discoveredCloudAppUser](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappuser?view=graph-rest-beta) collection | The list of users who access the app. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.discoveredCloudAppDetail",
  "category": "String",
  "displayName": "String",
  "domains": ["String"],
  "downloadNetworkTrafficInBytes": "Int64",
  "id": "String (identifier)",
  "ipAddressCount": "Int64",
  "lastSeenDateTime": "String (timestamp)",
  "riskScore": "Int64",
  "tags": ["String"],
  "transactionCount": "Int64",
  "uploadNetworkTrafficInBytes": "Int64",
  "userCount": "Int64"
}
```
