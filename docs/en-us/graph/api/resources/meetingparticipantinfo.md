<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/meetingparticipantinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-01-16 -->

# meetingParticipantInfo resource type

Namespace: microsoft.graph

Information about a participant in a meeting.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identity | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity information of the participant. |
| role | [onlineMeetingRole](#onlinemeetingrole-values) | Specifies the participant's role in the meeting. |
| upn | String | User principal name of the participant. |

### onlineMeetingRole values

The following table lists the members of an [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). Use the `Prefer: include-unknown-enum-members` request header to get the following values in this evolvable enum: `producer`, `coorganizer`.

| Value | Description |
| --- | --- |
| attendee | Participant's role is attendee. This value applies to all meetings. |
| presenter | Participant's role is presenter. This value applies to meetings with **allowedPresenter** set to `roleIsPresenter`, or a Teams live event. |
| producer | Participant's role is producer. This value applies to Teams live event only. |
| coorganizer | Participant's role is co-organizer. This value applies to all meetings except Teams live event. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

Tip

To set the **presenter** role of a meeting attendee when creating or updating an [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0), the value of **allowedPresenters** must also be set to `roleIsPresenter`.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "identity": {"@odata.type": "#microsoft.graph.identitySet"},
  "upn": "String",
  "role": "String"
}
```
