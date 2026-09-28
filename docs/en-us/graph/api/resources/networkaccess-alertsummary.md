<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-alertsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-31 -->

# alertSummary resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a summary of a specific [alert](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-alert?view=graph-rest-beta) severity and type detected by Global Secure Access.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alertType | microsoft.graph.networkaccess.alertType | The type of the alerts. Required. The possible values are: `unhealthyRemoteNetworks`, `unhealthyConnectors`, `deviceTokenInconsistency`, `crossTenantAnomaly`, `suspiciousProcess`, `threatIntelligenceTransactions`, `unknownFutureValue`, `webContentBlocked`, `malware`, `patientZero`, `dlp`, `fallback`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `webContentBlocked` , `malware` , `patientZero` , `dlp` , `fallback`. |
| count | Int64 | Total number of alerts with this specific severity and type. Required. |
| severity | microsoft.graph.networkaccess.alertSeverity | The severity of the alerts. Required. The possible values are: `informational`, `low`, `medium`, `high`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.alertSummary",
  "severity": "String",
  "alertType": "String",
  "count": "Integer"
}
```
