<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/itemactivitytimeset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# itemActivityTimeSet resource type

Namespace: microsoft.graph

The **itemActivityTimeSet** resource provides information about when an [activity](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) on an item took place.

> **Note:** Item activity records are currently only available on SharePoint and OneDrive for Business.

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| observedDateTime | DateTimeOffset | When the activity was observed to take place. |
| recordedDateTime | DateTimeOffset | When the observation was recorded on the service. |

The difference between **observed** and **recorded** times is especially important for offline collaboration scenarios. If a user comments on a file while offline, the time that they make the comment is set as the **observedDateTime**. At a later time when the user reconnects to the cloud and the changes get uploaded, that later time is set as the **recordedDateTime**.

## JSON representation

```json
{
  "observedDateTime": "String (timestamp)",
  "recordedDateTime": "String (timestamp)"
}
```
