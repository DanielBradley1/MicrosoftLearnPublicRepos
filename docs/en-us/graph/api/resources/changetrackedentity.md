<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-04 -->

# changeTrackedEntity resource type

Namespace: microsoft.graph

Represents an entity to track changes made to any supported [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0) and associated resource.

Base type of [openShift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0), [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0), and [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Stage for deletion](https://learn.microsoft.com/en-us/graph/api/changetrackedentity-stagefordeletion?view=graph-rest-1.0) | None | Stage the deletion of an [openShift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0), [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0), or [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0) instance in a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0) in draft mode. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the creator of the entity. |
| createdDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| id | String | Read-only. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the person who last modified the entity. |
| lastModifiedDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.changeTrackedEntity",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)"
}
```
