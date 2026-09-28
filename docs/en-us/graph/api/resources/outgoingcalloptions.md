<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/outgoingcalloptions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-20 -->

# outgoingCallOptions resource type

Namespace: microsoft.graph

Represents a class that contains the options for an outgoing call.

Inherits from [callOptions](https://learn.microsoft.com/en-us/graph/api/resources/calloptions?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| hideBotAfterEscalation | Boolean | Indicates whether to hide the app after the call is escalated. Inherited from [callOptions](https://learn.microsoft.com/en-us/graph/api/resources/calloptions?view=graph-rest-1.0). |
| isContentSharingNotificationEnabled | Boolean | Indicates whether content sharing notifications should be enabled for the call. Inherited from [callOptions](https://learn.microsoft.com/en-us/graph/api/resources/calloptions?view=graph-rest-1.0). |
| isDeltaRosterEnabled | Boolean | Indicates whether delta roster is enabled for the call. Inherited from [callOptions](https://learn.microsoft.com/en-us/graph/api/resources/calloptions?view=graph-rest-1.0). |
| isInteractiveRosterEnabled | Boolean | Indicates whether delta roster filtering by participant interactivity is enabled. Inherited from [callOptions](https://learn.microsoft.com/en-us/graph/api/resources/calloptions?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.outgoingCallOptions",
  "hideBotAfterEscalation": "Boolean",
  "isContentSharingNotificationEnabled": "Boolean",
  "isDeltaRosterEnabled": "Boolean",
  "isInteractiveRosterEnabled": "Boolean"
}
```
