<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-usageprofilingpoint?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-04-11 -->

# usageProfilingPoint resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a data point with traffic count statistics for different access types in Global Secure Access at a specific point in time.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| internetAccessTrafficCount | Int64 | The count of traffic requests directed to general internet destinations. |
| microsoft365AccessTrafficCount | Int64 | The count of traffic requests directed to Microsoft 365 services. |
| microsoftAccessTrafficCount | Int64 | The count of traffic requests directed to Microsoft services excluding Microsoft 365. |
| privateAccessTrafficCount | Int64 | The count of traffic requests directed to internal private network destinations. |
| timeStampDateTime | DateTimeOffset | The date and time of this data point. |
| totalTrafficCount | Int64 | The total count of all traffic requests across all access types. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.usageProfilingPoint",
  "timeStampDateTime": "String (timestamp)",
  "totalTrafficCount": "Integer",
  "microsoft365AccessTrafficCount": "Integer",
  "privateAccessTrafficCount": "Integer",
  "internetAccessTrafficCount": "Integer",
  "microsoftAccessTrafficCount": "Integer"
}
```
