<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-raimportcerts-certificateconnectorhealthmetricvalue?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# certificateConnectorHealthMetricValue resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Metric snapshot value returned in response to a GetHealthMetricTimeSeries request.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dateTime | DateTimeOffset | Timestamp for this metric data-point. |
| successCount | Int64 | Count of successful requests/operations. |
| failureCount | Int64 | Count of failed requests/operations. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.certificateConnectorHealthMetricValue",
  "dateTime": "String (timestamp)",
  "successCount": 1024,
  "failureCount": 1024
}
```
