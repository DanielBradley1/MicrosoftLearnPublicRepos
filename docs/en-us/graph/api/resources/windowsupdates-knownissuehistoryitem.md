<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-knownissuehistoryitem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# knownIssueHistoryItem resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the description text for the known issue, used to maintain historical records.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the post was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| body | [microsoft.graph.windowsUpdates.itemBody](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-itembody?view=graph-rest-beta) | Container for holding content and type. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.knownIssueHistoryItem",
  "createdDateTime": "String (timestamp)"
}
```
