<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-entitiessummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-31 -->

# entitiesSummary resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a summary of entities for Global Secure Access reporting.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceCount | Int64 | The number of devices in the summary. Required. |
| trafficType | microsoft.graph.networkaccess.trafficType | The type of network traffic summarized. Required. The possible values are: `internet`, `private`, `microsoft365`, `all`, `unknownFutureValue`. |
| userCount | Int64 | The number of users in the summary. Required. |
| workloadCount | Int64 | The number of workloads in the summary. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.entitiesSummary",
  "trafficType": "String",
  "userCount": "Integer",
  "deviceCount": "Integer",
  "workloadCount": "Integer"
}
```
