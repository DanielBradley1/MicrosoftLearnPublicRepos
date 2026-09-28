<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/recurrencerange?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# recurrenceRange resource type

Namespace: microsoft.graph

In a [patternedRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/patternedrecurrence?view=graph-rest-1.0) object, the **range** property defines the date range over which an event recurs. This shared object is also used for [calendar events](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) and [access package assignments](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0) in Microsoft Entra ID.

You can specify the date range for a recurring event in one of 3 ways depending on your scenario. While you must always specify a **startDate** value for the date range, you can specify a recurring event that ends by a specific date, or that doesn't end, or that ends after a specific number of occurrences. Note that the actual occurrences within the date range always follow the recurrence pattern that you specify for the recurring event. A recurring event is always defined by its [recurrencePattern](https://learn.microsoft.com/en-us/graph/api/resources/recurrencepattern?view=graph-rest-1.0) \(how frequently the event repeats\), and its **recurrenceRange** \(for how long the event repeats\).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| endDate | Date | The date to stop applying the recurrence pattern. Depending on the recurrence pattern of the event, the last occurrence of the meeting may not be this date. Required if **type** is `endDate`. |
| numberOfOccurrences | Int32 | The number of times to repeat the event. Required and must be positive if **type** is `numbered`. |
| recurrenceTimeZone | String | Time zone for the **startDate** and **endDate** properties. Optional. If not specified, the time zone of the event is used. |
| startDate | Date | The date to start applying the recurrence pattern. The first occurrence of the meeting may be this date or later, depending on the recurrence pattern of the event. Must be the same value as the **start** property of the recurring [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0). Required. |
| type | recurrenceRangeType | The recurrence range. The possible values are: `endDate`, `noEnd`, `numbered`. Required. |

Use the **type** property to specify the different types of **recurrenceRange**. Note the required properties for each type, as described in the following table.

| type property | Type of recurrence range | Description | Example | Required properties |
| :--- | :--- | :--- | :--- | :--- |
| `endDate` | Range with end date | Event repeats on all the days that fit the corresponding recurrence pattern between the **startDate** and **endDate** inclusive. | Repeat event in the date range between June 1, 2017 and June 15, 2017. | **type**, **startDate**, **endDate** |
| `noEnd` | Range without an end date | Event repeats on all the days that fit the corresponding recurrence pattern beginning on the **startDate**. | Repeat event in the date range starting on June 1, 2017 indefinitely. | **type**, **startDate** |
| `numbered` | Range with specific number of occurrences | Event repeats for the **numberOfOccurrences** based on the recurrence pattern beginning on the **startDate**. | Repeat event in the date range starting on June 1, 2017, for 10 occurrences. | **type**, **startDate**, **numberOfOccurrences** |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "endDate": "String (timestamp)",
  "numberOfOccurrences": 1024,
  "recurrenceTimeZone": "string",
  "startDate": "String (timestamp)",
  "type": "String"
}
```
