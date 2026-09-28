<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/recurrencepattern?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-08 -->

# recurrencePattern resource type

Namespace: microsoft.graph

In a [patternedRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/patternedrecurrence?view=graph-rest-1.0) object, the **pattern** property defines the frequency by which an event repeats. This shared object is also used for [calendar events](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) and [access package assignments](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0) in Microsoft Entra ID.

You can specify the recurrence pattern of a recurring event in one of 6 ways depending on your scenario. For each pattern type, specify the amount of time between occurrences. The actual occurrences of the recurring event always follow this pattern falling within the date range that you specify for the event. A recurring event is always defined by its **recurrencePattern** \(how frequently the event repeats\), and its [recurrenceRange](https://learn.microsoft.com/en-us/graph/api/resources/recurrencerange?view=graph-rest-1.0) \(over how long the event repeats\).

Use the **type** property to specify the different types of **recurrencePattern**, and the **interval** property to specify the time between occurrences, which can be in number of days, weeks, months, or years, depending on the **type**. Note which properties are required for each type, as described in the following table.

> **Note** Include only the properties that you need for a recurrence pattern. Any property that you include that does not have a supported value would result in an error.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dayOfMonth | Int32 | The day of the month on which the event occurs. Required if **type** is `absoluteMonthly` or `absoluteYearly`. |
| daysOfWeek | dayOfWeek collection | A collection of the days of the week on which the event occurs. The possible values are: `sunday`, `monday`, `tuesday`, `wednesday`, `thursday`, `friday`, `saturday`.  <br>If **type** is `relativeMonthly` or `relativeYearly`, and **daysOfWeek** specifies more than one day, the event falls on the first day that satisfies the pattern.  <br>Required if **type** is `weekly`, `relativeMonthly`, or `relativeYearly`. |
| firstDayOfWeek | dayOfWeek | The first day of the week. The possible values are: `sunday`, `monday`, `tuesday`, `wednesday`, `thursday`, `friday`, `saturday`. Default is `sunday`. Required if **type** is `weekly`. |
| index | weekIndex | Specifies on which instance of the allowed days specified in **daysOfWeek** the event occurs, counted from the first instance in the month. The possible values are: `first`, `second`, `third`, `fourth`, `last`. Default is `first`. Optional and used if **type** is `relativeMonthly` or `relativeYearly`. |
| interval | Int32 | The number of units between occurrences, where units can be in days, weeks, months, or years, depending on the **type**. Required. |
| month | Int32 | The month in which the event occurs. This is a number from 1 to 12. |
| type | recurrencePatternType | The recurrence pattern type: `daily`, `weekly`, `absoluteMonthly`, `relativeMonthly`, `absoluteYearly`, `relativeYearly`. Required. For more information, see [values of type property](#values-of-type-property). |

Important

For access reviews, only **dayOfMonth**, **interval**, and **type** \(`weekly`, `absoluteMonthly`\) properties are supported.

### Values of type property

| Value of type property | Description | Example | Required properties |
| :--- | :--- | :--- | :--- |
| `daily` | Event repeats based on the number of days specified by **interval** between occurrences. | Repeat event every 3 days. | **type**, **interval** |
| `weekly` | Event repeats on the same day or days of the week, based on the number of weeks between each set of occurrences. | Repeat event Monday and Tuesday of every other week. | **type**, **interval**, **daysOfWeek**, **firstDayOfWeek**  <br>  <br>**Note:** For access reviews, only **interval** and **type** properties are supported. |
| `absoluteMonthly` | Event repeats on the specified day of the month \(e.g. the 15th\), based on the number of months between occurrences. | Repeat event quarterly \(every 3 months\) on the 15th. | **type**, **interval**, **dayOfMonth**  <br>  <br>**Note:** For access reviews, only **interval**, **dayOfMonth**, and **type** properties are supported. |
| `relativeMonthly` | Event repeats on the specified day or days of the week, in the same relative position in the month, based on the number of months between occurrences. | Repeat event on the second Thursday or Friday every three months. | **type**, **interval**, **daysOfWeek** |
| `absoluteYearly` | Event repeats on the specified day and month, based on the number of years between occurrences. | Repeat event on the 15th of March every 3 years. | **type**, **interval**, **dayOfMonth**, **month** |
| `relativeYearly` | Event repeats on the specified day or days of the week, in the same relative position in a specific month of the year, based on the number of years between occurrences. | Repeat event on the second Thursday or Friday of every November every 3 years. | **type**, **interval**, **daysOfWeek**, **month** |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "dayOfMonth": 1024,
  "daysOfWeek": ["String"],
  "firstDayOfWeek": "String",
  "index": "String",
  "interval": 1024,
  "month": 1024,
  "type": "String"
}
```
