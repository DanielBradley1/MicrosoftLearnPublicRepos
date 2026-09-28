<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-retentionevent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# retentionEvent resource type

Namespace: microsoft.graph.security

Represents a trigger for event-based retention labels where start of the retention period is based on when a specific type of event occurs. To learn more about it, see [Start retention when an event occurs](https://learn.microsoft.com/en-us/microsoft-365/compliance/event-driven-retention).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List retentionEvents](https://learn.microsoft.com/en-us/graph/api/security-retentionevent-list?view=graph-rest-1.0) | [microsoft.graph.security.retentionEvent](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionevent?view=graph-rest-1.0) collection | Get a list of the [retentionEvent](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionevent?view=graph-rest-1.0) objects and their properties. |
| [Create retentionEvent](https://learn.microsoft.com/en-us/graph/api/security-retentionevent-post?view=graph-rest-1.0) | [microsoft.graph.security.retentionEvent](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionevent?view=graph-rest-1.0) | Create a new [retentionEvent](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionevent?view=graph-rest-1.0) object. |
| [Get retentionEvent](https://learn.microsoft.com/en-us/graph/api/security-retentionevent-get?view=graph-rest-1.0) | [microsoft.graph.security.retentionEvent](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionevent?view=graph-rest-1.0) | Read the properties and relationships of a [retentionEvent](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionevent?view=graph-rest-1.0) object. |
| [Delete retentionEvent](https://learn.microsoft.com/en-us/graph/api/security-retentionevent-delete?view=graph-rest-1.0) | None | Delete a [retentionEvent](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionevent?view=graph-rest-1.0) object. |
| [List retentionEventType](https://learn.microsoft.com/en-us/graph/api/security-retentioneventtype-list?view=graph-rest-1.0) | [microsoft.graph.security.retentionEventType](https://learn.microsoft.com/en-us/graph/api/resources/security-retentioneventtype?view=graph-rest-1.0) collection | Get the retentionEventType resources from the exapnd eventType navigation property. |
| [Create retentionEventType](https://learn.microsoft.com/en-us/graph/api/security-retentioneventtype-post?view=graph-rest-1.0) | [microsoft.graph.security.retentionEventType](https://learn.microsoft.com/en-us/graph/api/resources/security-retentioneventtype?view=graph-rest-1.0) | Add eventType by adding the relevant odata property when creating an event. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | The user who created the retentionEvent. |
| createdDateTime | DateTimeOffset | The date time when the retentionEvent was created. |
| description | String | Optional information about the event. |
| displayName | String | Name of the event. |
| eventPropagationResults | [microsoft.graph.security.eventPropagationResult](https://learn.microsoft.com/en-us/graph/api/resources/security-eventpropagationresult?view=graph-rest-1.0) collection | Represents the success status of a created event and additional information. |
| eventQueries | [microsoft.graph.security.eventQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-eventquery?view=graph-rest-1.0) collection | Represents the workload \(SharePoint Online, OneDrive for Business, Exchange Online\) and identification information associated with a retention event. |
| eventStatus | [microsoft.graph.security.retentionEventStatus](https://learn.microsoft.com/en-us/graph/api/resources/security-retentioneventstatus?view=graph-rest-1.0) | Status of event propogation to the scoped locations after the event has been created. |
| eventTriggerDateTime | DateTimeOffset | Optional time when the event should be triggered. |
| id | String | Represents the unique ID of the user who created the retentionEvent. [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity). |
| lastModifiedBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | The user who last modified the retentionEvent. |
| lastModifiedDateTime | DateTimeOffset | The latest date time when the retentionEvent was modified. |
| lastStatusUpdateDateTime | DateTimeOffset | Last time the status of the event was updated. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| retentionEventType | [microsoft.graph.security.retentionEventType](https://learn.microsoft.com/en-us/graph/api/resources/security-retentioneventtype?view=graph-rest-1.0) | Specifies the event that will start the retention period for labels that use this event type when an event is created. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.retentionEvent",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "eventQueries": [
    {
      "@odata.type": "microsoft.graph.security.eventQuery"
    }
  ],
  "eventTriggerDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "eventPropagationResults": [
    {
      "@odata.type": "microsoft.graph.security.eventPropagationResult"
    }
  ],
  "eventStatus": {
    "@odata.type": "microsoft.graph.security.retentionEventStatus"
  },
  "lastStatusUpdateDateTime": "String (timestamp)"
}
```
