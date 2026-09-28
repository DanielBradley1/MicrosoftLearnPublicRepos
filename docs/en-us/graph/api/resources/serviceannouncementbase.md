<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/serviceannouncementbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# serviceAnnouncementBase resource type

Namespace: microsoft.graph

This is an abstract base type for [serviceHealthIssue](https://learn.microsoft.com/en-us/graph/api/resources/servicehealthissue?view=graph-rest-1.0) and [serviceUpdateMessage](https://learn.microsoft.com/en-us/graph/api/resources/serviceupdatemessage?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| details | Collection\([keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-1.0)\) | More details about service event. This property doesn't support filters. |
| endDateTime | DateTimeOffset | The end time of the service event. |
| id | String | The ID of the service event. |
| lastModifiedDateTime | DateTimeOffset | The last modified time of the service event. |
| startDateTime | DateTimeOffset | The start time of the service event. |
| title | String | The title of the service event. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.serviceAnnouncementBase",
  "id": "String (identifier)",
  "startDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "title": "String",
  "details": [
    {
      "@odata.type": "microsoft.graph.keyValuePair"
    }
  ]
}
```
