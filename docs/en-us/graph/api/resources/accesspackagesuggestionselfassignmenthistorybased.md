<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesuggestionselfassignmenthistorybased?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# accessPackageSuggestionSelfAssignmentHistoryBased resource type

Namespace: microsoft.graph

Represents access package suggestions that are based on the user's own assignment history in [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0). This suggestion type helps users rediscover access packages they have previously been assigned to.

Inherits from [accessPackageSuggestionReason](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesuggestionreason?view=graph-rest-1.0).

In entitlement management, this subtype is configured in the **reasons** property of [accessPackageSuggestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesuggestion?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| lastAssignmentDateTime | DateTimeOffset | The date and time when the user was last assigned to this access package. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| pastAssignmentCount | Int32 | The number of times the user has been assigned to this access package in the past. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageSuggestionSelfAssignmentHistoryBased",
  "pastAssignmentCount": "Int32",
  "lastAssignmentDateTime": "String (timestamp)"
}
```
