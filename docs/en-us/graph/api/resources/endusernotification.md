<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/endusernotification?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# endUserNotification resource type

Namespace: microsoft.graph

Represents an end user notification.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-list-endusernotifications?view=graph-rest-1.0) | [endUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/endusernotification?view=graph-rest-1.0) collection | Get a list of [endUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/endusernotification?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/endusernotification-get?view=graph-rest-1.0) | [endUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/endusernotification?view=graph-rest-1.0) | Read the properties and relationships of an [endUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/endusernotification?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-1.0) | Identity of the user who created the notification. |
| createdDateTime | DateTimeOffset | Date and time when the notification was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| description | String | Description of the notification as defined by the user. |
| displayName | String | Name of the notification as defined by the user. |
| id | String | Unique identifier for the **endUserNotification** object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedBy | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-1.0) | Identity of the user who last modified the notification. |
| lastModifiedDateTime | DateTimeOffset | Date and time when the notification was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| notificationType | endUserNotificationType | Type of notification. The possible values are: `unknown`, `positiveReinforcement`, `noTraining`, `trainingAssignment`, `trainingReminder`, `unknownFutureValue`. |
| source | [simulationContentSource](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0#simulationcontentsource-values) | The source of the content. The possible values are: `unknown`, `global`, `tenant`, `unknownFutureValue`. |
| status | [simulationContentStatus](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0#simulationcontentstatus-values) | The status of the notification. The possible values are: `unknown`, `draft`, `ready`, `archive`, `delete`, `unknownFutureValue`. |
| supportedLocales | String collection | Supported locales for **endUserNotification** content. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.endUserNotification",
  "createdBy": {"@odata.type": "microsoft.graph.emailIdentity"},
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.emailIdentity"},
  "lastModifiedDateTime": "String (timestamp)",
  "notificationType": "String",
  "source": "String",
  "status": "String",
  "supportedLocales": ["String"]
}
```
