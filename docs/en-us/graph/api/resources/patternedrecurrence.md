<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/patternedrecurrence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# patternedRecurrence resource type

Namespace: microsoft.graph

In [accessReviewScheduleSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewschedulesettings?view=graph-rest-1.0) and [accessReviewHistoryScheduleSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistoryschedulesettings?view=graph-rest-1.0), the **recurrence** property uses **patternedRecurrence** to define the recurrence pattern and range. This shared object is also used to define the recurrence of [calendar events](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) and [access package assignments](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0) in Microsoft Entra ID.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| pattern | [recurrencePattern](https://learn.microsoft.com/en-us/graph/api/resources/recurrencepattern?view=graph-rest-1.0) | The frequency of an event.  <br>  <br>For access reviews:<br><br><li>Do not specify this property for a one-time access review. </li><br><br><li> Only <strong>interval</strong>, <strong>dayOfMonth</strong>, and <strong>type</strong> (<code>weekly</code>, <code>absoluteMonthly</code>) properties of <a href="https://learn.microsoft.com/en-us/graph/api/resources/recurrencepattern?view=graph-rest-1.0" data-linktype="relative-path">recurrencePattern</a> are supported.</li> |
| range | [recurrenceRange](https://learn.microsoft.com/en-us/graph/api/resources/recurrencerange?view=graph-rest-1.0) | The duration of an event. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "pattern": {"@odata.type": "microsoft.graph.recurrencePattern"},
  "range": {"@odata.type": "microsoft.graph.recurrenceRange"}
}
```
