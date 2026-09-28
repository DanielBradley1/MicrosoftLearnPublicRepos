<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partner-security-activitylog?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-08 -->

# activityLog resource type

Namespace: microsoft.graph.partner.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the activity undertaken by a partner and includes details of state transitions, who performed them, and when they occurred.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| statusFrom | microsoft.graph.partner.security.securityAlertStatus | The status of the alert before the status update activity by the partner. The possible values are: `active`, `resolved`, `investigating`, `unknownFutureValue`. |
| statusTo | microsoft.graph.partner.security.securityAlertStatus | The status of the alert after the status update activity by the partner. The possible values are: `active`, `resolved`, `investigating`, `unknownFutureValue`. |
| updatedBy | String | The UPN of the partner user who did the status update activity. This attribute is set by the system. |
| updatedDateTime | DateTimeOffset | The date and time for the status update activity. This attribute is set by the system. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.partner.security.activityLog",
  "statusFrom": "String",
  "statusTo": "String",
  "updatedBy": "String",
  "updatedDateTime": "String (timestamp)"
}
```
