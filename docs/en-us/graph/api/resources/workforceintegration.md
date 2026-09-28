<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workforceintegration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# workforceIntegration resource type

Namespace: microsoft.graph

Represents an instance of a workforce integration with shifts.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/workforceintegration-post?view=graph-rest-1.0) | [workforceIntegration](https://learn.microsoft.com/en-us/graph/api/resources/workforceintegration?view=graph-rest-1.0) | Create a new **workforceIntegration** object. |
| [List](https://learn.microsoft.com/en-us/graph/api/workforceintegration-list?view=graph-rest-1.0) | [workforceIntegration](https://learn.microsoft.com/en-us/graph/api/resources/workforceintegration?view=graph-rest-1.0) collection | Get the list of **workforceIntegration** objects associated with this schedule. |
| [Get](https://learn.microsoft.com/en-us/graph/api/workforceintegration-get?view=graph-rest-1.0) | [workforceIntegration](https://learn.microsoft.com/en-us/graph/api/resources/workforceintegration?view=graph-rest-1.0) | Read the properties and relationships of a **workforceIntegration** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/workforceintegration-update?view=graph-rest-1.0) | [workforceIntegration](https://learn.microsoft.com/en-us/graph/api/resources/workforceintegration?view=graph-rest-1.0) | Update a **workforceIntegration** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/workforceintegration-delete?view=graph-rest-1.0) | None | Delete a **workforceIntegration** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| apiVersion | Int32 | API version for the callback URL. Start with 1. |
| createdDateTime | DateTimeOffset | The date and time at which this **workforceIntegration** was first created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| displayName | String | Name of the workforce integration. |
| eligibilityFilteringEnabledEntities | eligibilityFilteringEnabledEntities | Support to view eligibility-filtered results. The possible values are: `none`, `swapRequest`, `offerShiftRequest`, `unknownFutureValue`, `timeOffReason`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `timeOffReason`. |
| encryption | [workforceIntegrationEncryption](https://learn.microsoft.com/en-us/graph/api/resources/workforceintegrationencryption?view=graph-rest-1.0) | The workforce integration encryption resource. |
| isActive | Boolean | Indicates whether this workforce integration is currently active and available. |
| supportedEntities | workforceIntegrationSupportedEntities | The Shifts entities supported for synchronous change notifications. Shifts call back to the provided URL when client changes occur to the entities specified in this property. By default, no entities are supported for change notifications. The possible values are: `none`, `shift`, `swapRequest`, `userShiftPreferences`, `openShift`, `openShiftRequest`, `offerShiftRequest`, `unknownFutureValue`, `timeCard`, `timeOffReason`, `timeOff`, `timeOffRequest`. Use the `Prefer: include-unknown-enum-members` request header to get the following values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `timeCard` , `timeOffReason` , `timeOff` , `timeOffRequest`. |
| url | String | Workforce Integration URL for callbacks from the Shifts service. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.workforceIntegration",
  "apiVersion": "Int32",
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "eligibilityFilteringEnabledEntities": "String",
  "encryption": {"@odata.type": "microsoft.graph.workforceIntegrationEncryption"},
  "id": "String (identifier)",
  "isActive": "Boolean",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "supportedEntities": "String",
  "url": "String"
}
```
