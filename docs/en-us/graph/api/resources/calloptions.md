<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/calloptions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-20 -->

# callOptions resource type

Namespace: microsoft.graph

Represents an abstract base class that contains the optional features for a call.

Base type of [incomingCallOptions](https://learn.microsoft.com/en-us/graph/api/resources/incomingcalloptions?view=graph-rest-1.0) and [outgoingCallOptions](https://learn.microsoft.com/en-us/graph/api/resources/outgoingcalloptions?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| hideBotAfterEscalation | Boolean | Indicates whether to hide the app after the call is escalated. |
| isContentSharingNotificationEnabled | Boolean | Indicates whether content sharing notifications should be enabled for the call. |
| isDeltaRosterEnabled | Boolean | Indicates whether delta roster is enabled for the call. |
| isInteractiveRosterEnabled | Boolean | Indicates whether delta roster filtering by participant interactivity is enabled. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.callOptions",
  "hideBotAfterEscalation": "Boolean",
  "isContentSharingNotificationEnabled": "Boolean",
  "isDeltaRosterEnabled": "Boolean",
  "isInteractiveRosterEnabled": "Boolean"
}
```
