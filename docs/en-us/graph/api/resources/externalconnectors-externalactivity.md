<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalactivity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# externalActivity resource type

Namespace: microsoft.graph.externalConnectors

Represents a record of a user interaction with an [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0) object.

Base type of [externalActivityResult](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalactivityresult?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| startDateTime | DateTimeOffset | The date and time when the particular activity occurred. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| type | microsoft.graph.externalConnectors.externalActivityType | The type of activity performed. The possible values are: `viewed`, `modified`, `created`, `commented`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| performedBy | [microsoft.graph.externalConnectors.identity](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-identity?view=graph-rest-1.0) | Represents an identity used to identify who is responsible for the activity. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.externalConnectors.externalActivity",
  "startDateTime": "String (timestamp)",
  "type": "String"
}
```
