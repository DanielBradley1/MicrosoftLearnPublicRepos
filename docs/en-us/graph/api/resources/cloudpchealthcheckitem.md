<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpchealthcheckitem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# cloudPcHealthCheckItem resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details of the Cloud PC connectivity health check item.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalDetails | string | Additional message for this health check. |
| displayName | string | The connectivity health check item name. |
| lastHealthCheckDateTime | DateTimeOffset | Timestamp when the last check occurs. The timestamp is shown in ISO 8601 format and Coordinated Universal Time \(UTC\). For example, midnight UTC on Jan 1, 2014 appears as `2014-01-01T00:00:00Z`. |
| result | [cloudPcConnectivityEventResult](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcconnectivityevent?view=graph-rest-beta#cloudpcconnectivityeventresult-values) | The result of this health check item. The possible values are: `unknown`, `success`, `failure`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcHealthCheckItem",
  "additionalDetails": "String",
  "displayName": "String",
  "lastHealthCheckDateTime": "String (timestamp)",
  "result": "String"
}
```
