<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attendancerecord?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# attendanceRecord resource type

Namespace: microsoft.graph

Contains information associated with an attendance record in a [meetingAttendanceReport](https://learn.microsoft.com/en-us/graph/api/resources/meetingattendancereport?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/attendancerecord-list?view=graph-rest-1.0) | [attendanceRecord](https://learn.microsoft.com/en-us/graph/api/resources/attendancerecord?view=graph-rest-1.0) collection | Get a list of [attendanceRecord](https://learn.microsoft.com/en-us/graph/api/resources/attendancerecord?view=graph-rest-1.0) objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attendanceIntervals | [attendanceInterval](https://learn.microsoft.com/en-us/graph/api/resources/attendanceinterval?view=graph-rest-1.0) collection | List of time periods between joining and leaving a meeting. |
| emailAddress | String | Email address of the user associated with this attendance record. |
| externalRegistrationInformation | [virtualEventExternalRegistrationInformation](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventexternalregistrationinformation?view=graph-rest-1.0) | The external information for a [virtualEventRegistration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0). |
| identity | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | The identity of the user associated with this attendance record. The specific type is one of the following derived types of [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0), depending on the user type: [communicationsUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsuseridentity?view=graph-rest-1.0), [azureCommunicationServicesUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/azurecommunicationservicesuseridentity?view=graph-rest-1.0). |
| registrationId | String | Unique identifier of a [virtualEventRegistration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0) that is available to all participants registered for the [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0). |
| role | String | Role of the attendee. The possible values are: `None`, `Attendee`, `Presenter`, and `Organizer`. |
| totalAttendanceInSeconds | Int32 | Total duration of the attendances in seconds. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.attendanceRecord",
  "attendanceIntervals": [{"@odata.type": "#microsoft.graph.attendanceInterval"}],
  "emailAddress": "String",
  "externalRegistrationInformation": {"@odata.type": "#microsoft.graph.virtualEventExternalRegistrationInformation"},
  "identity": {"@odata.type": "#microsoft.graph.identity"},
  "registrationId": "String",
  "role": "String",
  "totalAttendanceInSeconds": "Int32"
}
```
