<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-01-09 -->

# virtualEventWebinar resource type

Namespace: microsoft.graph

Contains information about a virtual event webinar.

Inherits from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| --- | --- | --- |
| [List](https://learn.microsoft.com/en-us/graph/api/virtualeventsroot-list-webinars?view=graph-rest-1.0) | [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) collection | Get the list of all [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) objects created in a tenant. |
| [Create](https://learn.microsoft.com/en-us/graph/api/virtualeventsroot-post-webinars?view=graph-rest-1.0) | [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) | Create a [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/virtualeventwebinar-get?view=graph-rest-1.0) | [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) | Read the properties and relationships of a [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/virtualeventwebinar-update?view=graph-rest-1.0) | [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) | Update the properties of a [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) object. |
| [Publish](https://learn.microsoft.com/en-us/graph/api/virtualeventwebinar-publish?view=graph-rest-1.0) | None | Publish a [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0). |
| [Cancel](https://learn.microsoft.com/en-us/graph/api/virtualeventwebinar-cancel?view=graph-rest-1.0) | None | Cancel a [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0). |
| [List by user role](https://learn.microsoft.com/en-us/graph/api/virtualeventwebinar-getbyuserrole?view=graph-rest-1.0) | [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) collection | Get a **virtualEventWebinar** collection where the signed-in user is either the organizer or a coorganizer. |
| [List by user ID and role](https://learn.microsoft.com/en-us/graph/api/virtualeventwebinar-getbyuseridandrole?view=graph-rest-1.0) | [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) collection | Get a **virtualEventWebinar** collection where the specified user is either the organizer or a coorganizer. |
| [Set external event information](https://learn.microsoft.com/en-us/graph/api/virtualevent-setexternaleventinformation?view=graph-rest-1.0) | None | Link external event information to a [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) or [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) by setting an **externalEventId**. |

### Roles required to act on virtualEventWebinar objects

The following table shows the roles that can perform various actions on webinars.

| Role | Create | Get | Update | Publish | Cancel | List in org | List by user role | List by user ID & role |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Organizer | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ | ✅ | ❌ |
| Co-organizer | ❌ | ✅ | ✅ | ❌ | ❌ | ❌ | ✅ | ❌ |
| Presenter | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ |
| Attendee | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ |
| Custom application | ❌ | ✅ | ❌ | ❌ | ❌ | ✅ | ❌ | ✅ |

## Properties

| Property | Type | Description |
| --- | --- | --- |
| audience | meetingAudience | To whom the webinar is visible. The possible values are: `everyone`, `organization`, and `unknownFutureValue`. |
| coOrganizers | [communicationsUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsuseridentity?view=graph-rest-1.0) collection | Identity information of coorganizers of the webinar. |
| createdBy | [communicationsIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/communicationsidentityset?view=graph-rest-1.0) | Identity information for the creator of the webinar. Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). |
| description | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | Description of the webinar. Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). |
| displayName | String | Display name of the webinar. Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). |
| endDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | End time of the webinar. The **timeZone** property *can* be set to any of the time zones currently supported by Windows. For details on how to get all available time zones using PowerShell, see [Get-TimeZone](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-timezone#example-3-get-all-available-time-zones). |
| externalEventInformation | [virtualEventExternalInformation](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventexternalinformation?view=graph-rest-1.0) collection | The external information of a webinar. Returned only for event organizers or coorganizers; otherwise, `null`. |
| startDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | Start time of the webinar. The **timeZone** property *can* be set to any of the time zones currently supported by Windows. For details on how to get all available time zones using PowerShell, see [Get-TimeZone](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-timezone#example-3-get-all-available-time-zones). |
| id | String | Unique identifier of the webinar. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isRegistrationRequired | Boolean | Indicates whether attendee registration is enabled for the webinar. Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). |
| settings | [virtualEventSettings](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsettings?view=graph-rest-1.0) | The webinar settings. Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). |
| status | virtualEventStatus | Status of the webinar. The possible values are: `draft`, `published`, `canceled`, and `unknownFutureValue`. Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| --- | --- | --- |
| registrationConfiguration | [virtualEventWebinarRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinarregistrationconfiguration?view=graph-rest-1.0) | Registration configuration of the webinar. |
| registrations | [virtualEventRegistration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0) collection | Registration records of the webinar. |
| sessions | [virtualEventSession](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsession?view=graph-rest-1.0) collection | Sessions of the webinar. Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.virtualEventWebinar",
  "audience": "String",
  "coOrganizers": [{"@odata.type": "microsoft.graph.communicationsUserIdentity"}],
  "createdBy": {"@odata.type": "microsoft.graph.communicationsIdentitySet"},
  "description": {"@odata.type": "microsoft.graph.itemBody"},
  "displayName": "String",
  "endDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "externalEventInformation" : [{"@odata.type": "microsoft.graph.virtualEventExternalInformation"}],
  "id": "String (identifier)",
  "isRegistrationRequired": "Boolean",
  "settings": {"@odata.type": "microsoft.graph.virtualEventSettings"},
  "startDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "status": "String"
}
```

## Related content

[List meetingAttendanceReports](https://learn.microsoft.com/en-us/graph/api/meetingattendancereport-list?view=graph-rest-1.0)
