<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-23 -->

# virtualEventTownhall resource type

Namespace: microsoft.graph

Represents information about a virtual event town hall.

Inherits from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/virtualeventsroot-list-townhalls?view=graph-rest-1.0) | [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) collection | Get the list of all [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) objects created in a tenant. |
| [Create](https://learn.microsoft.com/en-us/graph/api/virtualeventsroot-post-townhalls?view=graph-rest-1.0) | [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) | Create a new [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/virtualeventtownhall-get?view=graph-rest-1.0) | [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) | Read the properties and relationships of a [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/virtualeventtownhall-update?view=graph-rest-1.0) | [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) | Update the properties of a [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) object. |
| [Publish](https://learn.microsoft.com/en-us/graph/api/virtualeventtownhall-publish?view=graph-rest-1.0) | None | Publish a [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0). |
| [Cancel](https://learn.microsoft.com/en-us/graph/api/virtualeventtownhall-cancel?view=graph-rest-1.0) | None | Cancel a [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0). |
| [List by user role](https://learn.microsoft.com/en-us/graph/api/virtualeventtownhall-getbyuserrole?view=graph-rest-1.0) | [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) collection | Get a list of **virtualEventTownhall** objects where the signed-in user is either the organizer or a coorganizer. |
| [List by user ID and role](https://learn.microsoft.com/en-us/graph/api/virtualeventtownhall-getbyuseridandrole?view=graph-rest-1.0) | [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) collection | Get a list of **virtualEventTownhall** objects where the specified user is either the organizer or a coorganizer. |
| [Set external event information](https://learn.microsoft.com/en-us/graph/api/virtualevent-setexternaleventinformation?view=graph-rest-1.0) | None | Link external event information to a [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) or [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) by setting an **externalEventId**. \] |

### Roles required to act on virtualEventTownhall objects

The following table shows the roles that can perform various actions on virtual event town halls.

| Role | Create | Get | Update | Publish | Cancel |
| --- | --- | --- | --- | --- | --- |
| Organizer | ✅ | ✅ | ✅ | ✅ | ✅ |
| Co-organizer | ❌ | ✅ | ✅ | ❌ | ❌ |
| Presenter | ❌ | ✅ | ❌ | ❌ | ❌ |
| Attendee | ❌ | ✅ | ❌ | ❌ | ❌ |
| Custom application | ❌ | ✅ | ❌ | ❌ | ❌ |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| audience | meetingAudience | The audience to whom the town hall is visible. The possible values are: `everyone`, `organization`, and `unknownFutureValue`. |
| capacity | Int32 | Represents the expected number of attendees for the town hall. |
| coOrganizers | [communicationsUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsuseridentity?view=graph-rest-1.0) collection | Identity information of the coorganizers of the town hall. |
| createdBy | [communicationsIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/communicationsidentityset?view=graph-rest-1.0) | Identity information of the creator of the town hall. Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). Read-only. |
| description | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | Description of the town hall. Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). |
| displayName | String | Display name of the town hall. Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). |
| endDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | Date and time when the town hall ends. The **timeZone** property *can* be set to any of the time zones currently supported by Windows. For details on how to get all available time zones using PowerShell, see [Get-TimeZone](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-timezone#example-3-get-all-available-time-zones). Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). |
| externalEventInformation | [virtualEventExternalInformation](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventexternalinformation?view=graph-rest-1.0) collection | The external information of a town hall. Returned only for event organizers or coorganizers; otherwise, `null`. |
| id | String | Unique identifier of the town hall. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Read-only. |
| invitedAttendees | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) collection | The attendees invited to the town hall. The supported identities are: [communicationsUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsuseridentity?view=graph-rest-1.0) and [communicationsGuestIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsguestidentity?view=graph-rest-1.0). |
| isInviteOnly | Boolean | Indicates whether the town hall is only open to invited people and groups within your organization. The **isInviteOnly** property can only be `true` if the value of the **audience** property is set to `organization`. |
| isRegistrationRequired | Boolean | Indicates whether attendee registration is enabled for the town hall. Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). |
| settings | [virtualEventSettings](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsettings?view=graph-rest-1.0) | The virtual event settings. |
| startDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | Date and time when the town hall starts. The **timeZone** property *can* be set to any of the time zones currently supported by Windows. For details on how to get all available time zones using PowerShell, see [Get-TimeZone](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-timezone#example-3-get-all-available-time-zones). Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). |
| status | virtualEventStatus | Status of the town hall. The possible values are: `draft`, `published`, `canceled`, and `unknownFutureValue`. Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| presenters | [virtualEventPresenter](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter?view=graph-rest-1.0) collection | Presenters' information of the town hall. Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). |
| registrationConfiguration | [virtualEventTownhallRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhallregistrationconfiguration?view=graph-rest-1.0) | Registration configuration of the town hall. |
| registrations | [virtualEventRegistration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0) collection | Registration records of the town hall. |
| sessions | [virtualEventSession](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsession?view=graph-rest-1.0) collection | Sessions of the town hall. Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.virtualEventTownhall",
  "audience": "String",
  "capacity": "Int32",
  "coOrganizers": [{"@odata.type": "microsoft.graph.communicationsUserIdentity"}],
  "createdBy": {"@odata.type": "microsoft.graph.communicationsIdentitySet"},
  "description": {"@odata.type": "microsoft.graph.itemBody"},
  "displayName": "String",
  "endDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "id": "String (identifier)",
  "invitedAttendees": [{"@odata.type": "microsoft.graph.identity"}],
  "isInviteOnly": "Boolean",
  "isRegistrationRequired": "Boolean",
  "settings": {"@odata.type": "microsoft.graph.virtualEventSettings"},
  "startDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "status": "String"
}
```
