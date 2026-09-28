<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-04 -->

# dayNote resource type

Namespace: microsoft.graph

Represents a note relevant for a specific day on a Teams schedule.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/schedule-list-daynotes?view=graph-rest-1.0) | [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-1.0) collection | Get a list of the [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/schedule-post-daynotes?view=graph-rest-1.0) | [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-1.0) | Create a new [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/daynote-get?view=graph-rest-1.0) | [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-1.0) | Read the properties and relationships of a [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/daynote-update?view=graph-rest-1.0) | [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-1.0) | Update the properties of a [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/schedule-delete-daynotes?view=graph-rest-1.0) | None | Delete a [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | ID of the day note. |
| dayNoteDate | Date | The date of the day note. |
| draftDayNote | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The draft version of this day note that is viewable by managers. Only contentType text is supported. |
| sharedDayNote | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The shared version of this day note that is viewable by both employees and managers. Only contentType text is supported. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.dayNote",
  "id": "String (identifier)",
  "dayNoteDate": "Date",
  "sharedDayNote": {
    "@odata.type": "microsoft.graph.itemBody"
  },
  "draftDayNote": {
    "@odata.type": "microsoft.graph.itemBody"
  }
}
```
