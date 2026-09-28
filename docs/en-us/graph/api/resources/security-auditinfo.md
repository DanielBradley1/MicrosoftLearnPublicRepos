<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-auditinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-20 -->

# auditInfo resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents audit metadata, including the user or application and timestamps for creation or modification actions. This resource tracks who performed an action and when it occurred.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| by | String | Display name of the user or application that performed the action. |
| dateTime | DateTimeOffset | Timestamp of the action. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.auditInfo",
  "by": "String",
  "dateTime": "String (timestamp)"
}
```
