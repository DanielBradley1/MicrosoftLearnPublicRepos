<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrantbase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# meetingRegistrantBase resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a base meeting registrant who enrolled in an online meeting.

Base type of [meetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrant?view=graph-rest-beta) and [externalMeetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistrant?view=graph-rest-beta).

Tip

This is an abstract type and cannot be used directly. Use the derived type [meetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrant?view=graph-rest-beta) or [externalMeetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistrant?view=graph-rest-beta) instead.

Caution

The meeting registrant API is deprecated and will stop returning data on **December 12, 2024**. Please use the new [webinar APIs](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-beta). For more information, see [Deprecation of the Microsoft Graph meeting registration beta APIs](https://devblogs.microsoft.com/microsoft365dev/deprecation-of-the-microsoft-graph-meeting-registration-beta-apis/).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the registrant. Read-only. |
| joinWebUrl | String | A unique web URL for the registrant to join the meeting. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.meetingRegistrantBase",
  "id": "String (identifier)",
  "joinWebUrl": "String"
}
```
