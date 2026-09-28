<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/threatassessmentresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# threatAssessmentResult resource type

Represents a threat assessment result item.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | The threat assessment result ID is a globally unique identifier \(GUID\). |
| message | String | The result message for each threat assessment. |
| resultType | [threatAssessmentResultType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#threatassessmentresulttype-values) | The threat assessment result type. The possible values are: `checkPolicy`, `rescan`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "message": "String",
  "resultType": "String"
}
```
