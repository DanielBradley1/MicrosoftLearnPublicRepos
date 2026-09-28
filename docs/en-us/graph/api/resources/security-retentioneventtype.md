<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-retentioneventtype?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# retentionEventType resource type

Namespace: microsoft.graph.security

Represents a single group for the same type of retention events.

When a [retention event](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionevent?view=graph-rest-1.0) is created, it's associated with a specific event type that in turn is associated with a [retention label](https://learn.microsoft.com/en-us/graph/api-reference/v1.0/resources/security-retentionlabel.md). Only content with that retention label applied will be retained for the specified retention period. For details, see [Start retention when an event occurs](https://learn.microsoft.com/en-us/microsoft-365/compliance/event-driven-retention).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-retentioneventtype-list?view=graph-rest-1.0) | [microsoft.graph.security.retentionEventType](https://learn.microsoft.com/en-us/graph/api/resources/security-retentioneventtype?view=graph-rest-1.0) collection | Get a list of the [retentionEventType](https://learn.microsoft.com/en-us/graph/api/resources/security-retentioneventtype?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-retentioneventtype-post?view=graph-rest-1.0) | [microsoft.graph.security.retentionEventType](https://learn.microsoft.com/en-us/graph/api/resources/security-retentioneventtype?view=graph-rest-1.0) | Create a new [retentionEventType](https://learn.microsoft.com/en-us/graph/api/resources/security-retentioneventtype?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-retentioneventtype-get?view=graph-rest-1.0) | [microsoft.graph.security.retentionEventType](https://learn.microsoft.com/en-us/graph/api/resources/security-retentioneventtype?view=graph-rest-1.0) | Read the properties and relationships of a [retentionEventType](https://learn.microsoft.com/en-us/graph/api/resources/security-retentioneventtype?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-retentioneventtype-update?view=graph-rest-1.0) | [microsoft.graph.security.retentionEventType](https://learn.microsoft.com/en-us/graph/api/resources/security-retentioneventtype?view=graph-rest-1.0) | Update the properties of a [retentionEventType](https://learn.microsoft.com/en-us/graph/api/resources/security-retentioneventtype?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-retentioneventtype-delete?view=graph-rest-1.0) | None | Delete a [retentionEventType](https://learn.microsoft.com/en-us/graph/api/resources/security-retentioneventtype?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | The user who created the retentionEventType. |
| createdDateTime | DateTimeOffset | The date time when the retentionEventType was created. |
| description | String | Optional information about the event type. |
| displayName | String | Name of the event type. |
| id | String | Represents the unique ID of the user who created the retentionEventType. [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity). |
| lastModifiedBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | The user who last modified the retentionEventType. |
| lastModifiedDateTime | DateTimeOffset | The latest date time when the retentionEventType was modified. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.retentionEventType",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)"
}
```
