<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrationbase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# meetingRegistrationBase resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The meeting registration API is deprecated and will stop returning data on **Decemeber 31, 2024**. Please use the new [webinar APIs](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-beta). For more information, see [Deprecation of the Microsoft Graph meeting registration beta APIs](https://devblogs.microsoft.com/microsoft365dev/deprecation-of-the-microsoft-graph-meeting-registration-beta-apis/).

Represents base registration details of an online meeting.

Base type of [meetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta) and [externalMeetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistration?view=graph-rest-beta).

Tip

This is an abstract type and cannot be used directly. Use the derived type [meetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta) or [externalMeetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistration?view=graph-rest-beta) instead.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedRegistrant | [meetingAudience](#meetingaudience-values) | Specifies who can register for the meeting. |

### meetingAudience values

| Value | Description |
| --- | --- |
| everyone | Everyone can register for the meeting. |
| organization | Everyone in the organizer’s organization can register for the meeting. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| registrants | [meetingRegistrantBase](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrantbase?view=graph-rest-beta) collection | Registrants of the online meeting. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.meetingRegistrationBase",
  "allowedRegistrant": "String",

  "registrants": [{ "@odata.type": "microsoft.graph.meetingRegistrantBase" }]
}
```
