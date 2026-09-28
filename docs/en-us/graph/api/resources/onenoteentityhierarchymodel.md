<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onenoteentityhierarchymodel?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# onenoteEntityHierarchyModel resource type

Namespace: microsoft.graph

A base type for OneNote entities.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the notebook. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user, device, and application that created the item. Read-only. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user, device, and application that created the item. Read-only. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the notebook was last modified. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "string",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)"
}
```
