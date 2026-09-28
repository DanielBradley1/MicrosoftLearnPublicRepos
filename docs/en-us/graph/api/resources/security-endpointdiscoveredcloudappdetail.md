<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-endpointdiscoveredcloudappdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-26 -->

# endpointDiscoveredCloudAppDetail resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the resources available for endpoints that access discovered apps.

Inherits from [discoveredCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-endpointdiscoveredcloudappdetail-get?view=graph-rest-beta) | [microsoft.graph.security.endpointDiscoveredCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/security-endpointdiscoveredcloudappdetail?view=graph-rest-beta) | Get the details of all [the discovered apps](https://learn.microsoft.com/en-us/graph/api/resources/security-endpointdiscoveredcloudappdetail?view=graph-rest-beta) for a specific stream or endpoint. |
| [List devices](https://learn.microsoft.com/en-us/graph/api/security-endpointdiscoveredcloudappdetail-list-devices?view=graph-rest-beta) | [microsoft.graph.security.discoveredCloudAppDevice](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdevice?view=graph-rest-beta) collection | Get a list of [devices](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdevice?view=graph-rest-beta) that access a discovered cloud app. |

For more API operations about discovered cloud app details, see [discoveredCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| category | microsoft.graph.security.appCategory | The list of category of discovered apps. The possible values are: `security`, `collaboration`, `hostingServices`, `onlineMeetings`, `newsAndEntertainment`, `eCommerce`, `education`, `cloudStorage`, `marketing`, `operationsManagement`, `health`, `advertising`, `productivity`, `accountingAndFinance`, `contentManagement`, `contentSharing`, `businessManagement`, `communications`, `dataAnalytics`, `businessIntelligence`, `webemail`, `codeHosting`, `webAnalytics`, `socialNetwork`, `crm`, `forums`, `humanResourceManagement`, `transportationAndTravel`, `productDesign`, `sales`, `cloudComputingPlatform`, `projectManagement`, `personalInstantMessaging`, `developmentTools`, `itServices`, `supplyChainAndLogistics`, `propertyManagement`, `customerSupport`, `internetOfThings`, `vendorManagementSystems`, `websiteMonitoring`, `generativeAi`, `unknown`, `unknownFutureValue`, `aiModelProvider`, `mcpServer`, `clientAiApp`. Use the `Prefer: include-unknown-enum-members` request header to get the following values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `aiModelProvider`, `mcpServer`, `clientAiApp`. Inherited from [discoveredCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta). |
| deviceCount | Int64 | The number of devices that accessed the discovered app. |
| displayName | String | The name of the discovered cloud app. Inherited from [discoveredCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta). |
| domains | String collection | The list of domains identified as belonging to the discovered app. Inherited from [discoveredCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta). |
| downloadNetworkTrafficInBytes | Int64 | The amount of download traffic from the app. Inherited from [discoveredCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta). |
| id | String | The ID of the discovered app. Inherited from [discoveredCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta). |
| ipAddressCount | Int64 | The count of IP addresses that accessed the discovered app. Inherited from [discoveredCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta). |
| lastSeenDateTime | DateTimeOffset | The date and time when the app was last seen. The Timestamp represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [discoveredCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta). |
| riskScore | Int64 | The risk score of the discovered app. Inherited from [discoveredCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta). |
| tags | String collection | A list of tags applied to a discovered app. Inherited from [discoveredCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta). |
| transactionCount | Int64 | The total transanctions on the discovered app. Inherited from [discoveredCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta). |
| uploadNetworkTrafficInBytes | Int64 | The upload traffic on the discovered app. Inherited from [discoveredCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta). |
| userCount | Int64 | The count of users who access the discovered app. Inherited from [discoveredCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appInfo | [microsoft.graph.security.discoveredCloudAppInfo](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappinfo?view=graph-rest-beta) | Represents the discovered app details. Inherited from [discoveredCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta). |
| devices | [microsoft.graph.security.discoveredCloudAppDevice](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdevice?view=graph-rest-beta) collection | Represents the devices that access the discovered apps. |
| ipAddresses | [microsoft.graph.security.discoveredCloudAppIPAddress](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappipaddress?view=graph-rest-beta) collection | Represents the IP addressses that access the discovered apps. Inherited from [discoveredCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta). |
| users | [microsoft.graph.security.discoveredCloudAppUser](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappuser?view=graph-rest-beta) collection | Represents the users who access the discovered apps. Inherited from [discoveredCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdetail?view=graph-rest-beta). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.endpointDiscoveredCloudAppDetail",
  "category": "String",
  "deviceCount": "Int64",
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
