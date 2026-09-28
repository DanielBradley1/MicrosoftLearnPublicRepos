<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/organizermeetinginfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# organizerMeetingInfo resource type

Namespace: microsoft.graph

Contains details about the meeting organizer.

To join an existing meeting, you must either provide a combination of the organizerMeetingInfo and the [chatInfo](https://learn.microsoft.com/en-us/graph/api/resources/chatinfo?view=graph-rest-1.0) resource types, or the [tokenMeetingInfo](https://learn.microsoft.com/en-us/graph/api/resources/tokenmeetinginfo?view=graph-rest-1.0) resource type by itself.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| organizer | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The organizer Microsoft Entra identity. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "organizer": { "@odata.type": "#microsoft.graph.identitySet" }
}
```
