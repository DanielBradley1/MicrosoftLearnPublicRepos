<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-alertfrequencypoint?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-31 -->

# alertFrequencyPoint resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a summary of all [alert](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-alert?view=graph-rest-beta) severities in a specific day detected by Global Secure Access.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| highSeverityCount | Int64 | Total number of high alert severity. Required. |
| informationalSeverityCount | Int64 | Total number of informational alert severity. Required. |
| lowSeverityCount | Int64 | Total number of low alert severity. Required. |
| mediumSeverityCount | Int64 | Total number of medium alert severity. Required. |
| timeStampDateTime | DateTimeOffset | The time bucket for counting the alert severities. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.alertFrequencyPoint",
  "timeStampDateTime": "String (timestamp)",
  "highSeverityCount": "Integer",
  "mediumSeverityCount": "Integer",
  "lowSeverityCount": "Integer",
  "informationalSeverityCount": "Integer"
}
```
