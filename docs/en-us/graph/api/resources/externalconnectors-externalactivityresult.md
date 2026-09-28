<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalactivityresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# externalActivityResult resource type

Namespace: microsoft.graph.externalConnectors

Represents the result of processing an [externalActivity](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalactivity?view=graph-rest-1.0). A `null` **error** property in the response object indicates a successful request.

Inherits from [externalActivity](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalactivity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| error | [microsoft.graph.publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | Error information that explains the failure to process an external activity. |
| startDateTime | DateTimeOffset | The date and time when the particular activity occurred. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [externalActivity](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalactivity?view=graph-rest-1.0). |
| type | microsoft.graph.externalConnectors.externalActivityType | The type of activity performed. The possible values are: `viewed`, `modified`, `created`, `commented`, `unknownFutureValue`. Inherited from [externalActivity](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalactivity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| performedBy | [microsoft.graph.externalConnectors.identity](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-identity?view=graph-rest-1.0) | Represents an identity used to identify who is responsible for the activity. Inherited from [externalActivity](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalactivity?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.externalConnectors.externalActivityResult",
  "error": {
    "@odata.type": "microsoft.graph.publicError"
  },
  "startDateTime": "String (timestamp)",
  "type": "String"
}
```
