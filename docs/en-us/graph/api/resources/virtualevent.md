<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-23 -->

# virtualEvent resource type

Namespace: microsoft.graph

Represents an abstract base type for a virtual event. Base type of [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) and [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

Tip

This is an abstract type and can't be used directly. Use the derived types [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) or [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) instead.

## Methods

| Method | Return Type | Description |
| --- | --- | --- |
| [Set external event information](https://learn.microsoft.com/en-us/graph/api/virtualevent-setexternaleventinformation?view=graph-rest-1.0) | None | Link external event information to a [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) or [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) by setting an **externalEventId**. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [communicationsIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/communicationsidentityset?view=graph-rest-1.0) | The identity information for the creator of the virtual event. Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). |
| description | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | A description of the virtual event. |
| displayName | String | The display name of the virtual event. |
| endDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The end time of the virtual event. The **timeZone** property *can* be set to any of the time zones currently supported by Windows. For details on how to get all available time zones using PowerShell, see [Get-TimeZone](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-timezone#example-3-get-all-available-time-zones). |
| externalEventInformation | [virtualEventExternalInformation](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventexternalinformation?view=graph-rest-1.0) collection | The external information of a virtual event. Returned only for event organizers or coorganizers; otherwise, `null`. |
| id | String | The unique identifier of the virtual event. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isRegistrationRequired | Boolean | Indicates whether attendee registration is enabled for the virtual event. |
| settings | [virtualEventSettings](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsettings?view=graph-rest-1.0) | The virtual event settings. |
| startDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | Start time of the virtual event. The **timeZone** property *can* be set to any of the time zones currently supported by Windows. For details on how to get all available time zones using PowerShell, see [Get-TimeZone](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-timezone#example-3-get-all-available-time-zones). |
| status | virtualEventStatus | The status of the virtual event. The possible values are: `draft`, `published`, `canceled`, and `unknownFutureValue`. |

Note

The **isRegistrationRequired** property controls whether the virtual event uses the registration workflow. When **isRegistrationRequired** is `false`, registration-related APIs can still be invoked. However, these calls don't trigger the full registration experience. Instead, they behave as an add-to-calendar action, allowing attendees to add the event to their calendar without completing a registration process. For webinars, registration is enabled by default \(**isRegistrationRequired** is `true`\). For town halls, registration isn't enabled by default. If registration is required for a town hall, the organizer must explicitly set **isRegistrationRequired** to `true` when configuring the virtual event.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| presenters | [virtualEventPresenter](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter?view=graph-rest-1.0) collection | The virtual event presenters. |
| sessions | [virtualEventSession](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsession?view=graph-rest-1.0) collection | The sessions for the virtual event. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.virtualEvent",
  "createdBy": {
    "@odata.type": "microsoft.graph.communicationsIdentitySet"
  },
  "description": {
    "@odata.type": "microsoft.graph.itemBody"
  },
  "displayName": "String",
  "endDateTime": {
    "@odata.type": "microsoft.graph.dateTimeTimeZone"
  },
  "externalEventInformation" : [{
    "@odata.type": "microsoft.graph.virtualEventExternalInformation"
  }],
  "id": "String (identifier)",
  "isRegistrationRequired": "Boolean",
  "settings": {
    "@odata.type": "microsoft.graph.virtualEventSettings"
  },
  "startDateTime": {
    "@odata.type": "microsoft.graph.dateTimeTimeZone"
  },
  "status": "String"
}
```
