<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/deltaparticipants?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# deltaParticipants resource type

Namespace: microsoft.graph

Represents a notification for the creation, update, or deletion of a [participant](https://learn.microsoft.com/en-us/graph/api/resources/participant?view=graph-rest-1.0) in a meeting. This resource is published by communications servers as a notification of participant changes since the last update.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| sequenceNumber | Int64 | The sequence number for the roster update that is used to identify the notification order. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| participants | [participant](https://learn.microsoft.com/en-us/graph/api/resources/participant?view=graph-rest-1.0) collection | The collection of participants that were updated since the last roster update. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.deltaParticipants",
  "sequenceNumber": "Int64"
}
```
