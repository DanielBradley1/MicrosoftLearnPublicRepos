<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudapplicationreport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# cloudApplicationReport resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Global Secure Access report with network traffic data and metadata of a catalog application. This information is returned by the [getCloudApplicationReport](https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-getcloudapplicationreport?view=graph-rest-beta) API.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| categories | String collection | The list of categories for the application. Supported values are: `Collaboration`, `Business Management`, `Consumer`, `Content management`, `CRM`, `Data services`, `Developer services`, `E-commerce`, `Education`, `ERP`, `Finance`, `Health`, `Human resources`, `IT infrastructure`, `Mail`, `Management`, `Marketing`, `Media`, `Productivity`, `Project management`, `Telecommunications`, `Tools`, `Travel`, and `Web design & hosting`. |
| cloudApplicationCatalogId | String | The ID of the application in the SaaS application catalog. |
| complianceScore | Int32 | The compliance score of the application. |
| deviceCount | Int32 | Number of devices under this application. |
| firstAccessDateTime | DateTimeOffset | Timestamp of the first access to the application. |
| generalScore | Int32 | The general score of the application. |
| lastAccessDateTime | DateTimeOffset | Timestamp of the last access to the application. |
| legalScore | Int32 | The legal score of the application. |
| name | String | The name of the application \(e.g., ChatGPT, Salesforce, Bing\). |
| riskScore | Int32 | The risk score of the application. |
| securityScore | Int32 | The security score of the application. |
| totalBytesReceived | Int64 | Total bytes received from the application. |
| totalBytesSent | Int64 | Total bytes sent to the application. |
| trafficType | microsoft.graph.networkaccess.trafficType | The type of traffic. The possible values are: `internet`, `private`, `microsoft365`, `all`, `unknownFutureValue`. |
| transactionCount | Int32 | Number of transactions under this application. |
| userCount | Int32 | Number of users under this application. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.cloudApplicationReport",
  "trafficType": "String",
  "firstAccessDateTime": "String (timestamp)",
  "lastAccessDateTime": "String (timestamp)",
  "transactionCount": "Integer",
  "userCount": "Integer",
  "deviceCount": "Integer",
  "totalBytesSent": "Integer",
  "totalBytesReceived": "Integer",
  "cloudApplicationCatalogId": "String",
  "name": "String",
  "generalScore": "Integer",
  "riskScore": "Integer",
  "complianceScore": "Integer",
  "legalScore": "Integer",
  "categories": [ "String" ],
  "securityScore": "Integer"
}
```
