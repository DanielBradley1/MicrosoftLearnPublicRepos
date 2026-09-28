<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# bookingCustomQuestion resource type

Namespace: microsoft.graph

Represents a custom question for a [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-list-customquestions?view=graph-rest-1.0) | [bookingCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion?view=graph-rest-1.0) collection | Get a list of the [bookingCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-customquestions?view=graph-rest-1.0) | [bookingCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion?view=graph-rest-1.0) | Create a new [bookingCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/bookingcustomquestion-get?view=graph-rest-1.0) | [bookingCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion?view=graph-rest-1.0) | Read the properties and relationships of a [bookingCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/bookingcustomquestion-update?view=graph-rest-1.0) | [bookingCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion?view=graph-rest-1.0) | Update the properties of a [bookingCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/bookingcustomquestion-delete?view=graph-rest-1.0) | None | Delete a [bookingCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| answerInputType | answerInputType | The expected answer type. The possible values are: `text`, `radioButton`, `unknownFutureValue`. |
| answerOptions | String collection | List of possible answer values. |
| createdDateTime | DateTimeOffset | The date, time, and time zone when the custom question was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| displayName | String | The question. |
| id | String | The ID of the custom question. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastUpdatedDateTime | DateTimeOffset | The date, time, and time zone when the custom question was last updated. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.bookingCustomQuestion",
  "answerInputType": "String",
  "answerOptions": ["String"],
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "id": "String (identifier)",
  "lastUpdatedDateTime": "String (timestamp)"
}
```
