<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-enterpriseapplicationreport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-29 -->

# enterpriseApplicationReport resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Global Secure Access report with network traffic data and metadata for an enterprise application. This information is returned by the [getEnterpriseApplicationReport](https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-getenterpriseapplicationreport?view=graph-rest-beta) API.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessType | microsoft.graph.networkaccess.accessType | The type of accessed application. The possible values are: `quickAccess`, `privateAccess`, `unknownFutureValue`, `appAccess`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `appAccess`. |
| applicationId | String | The unique identifier for the enterprise application \(`appId`\) in Microsoft Entra ID. |
| deviceCount | Int32 | Number of devices that accessed this application. |
| firstAccessDateTime | DateTimeOffset | Timestamp of the first access to the application. |
| lastAccessDateTime | DateTimeOffset | Timestamp of the last access to the application. |
| totalBytesReceived | Int64 | Total bytes received from the application. |
| totalBytesSent | Int64 | Total bytes sent to the application. |
| trafficType | microsoft.graph.networkaccess.trafficType | The type of traffic. The possible values are: `internet`, `private`, `microsoft365`, `all`, `unknownFutureValue`. |
| transactionCount | Int32 | Number of transactions to this application. |
| userCount | Int32 | Number of users that accessed this application. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.enterpriseApplicationReport",
  "trafficType": "String",
  "applicationId": "String",
  "firstAccessDateTime": "String (timestamp)",
  "lastAccessDateTime": "String (timestamp)",
  "transactionCount": "Integer",
  "userCount": "Integer",
  "deviceCount": "Integer",
  "totalBytesSent": "Integer",
  "totalBytesReceived": "Integer",
  "accessType": "String"
}
```
