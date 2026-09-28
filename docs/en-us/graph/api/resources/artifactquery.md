<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/artifactquery?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# artifactQuery resource type

Namespace: microsoft.graph

Contains an expression that specifies the criteria for search.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| artifactType | [restorableArtifact](https://learn.microsoft.com/en-us/graph/api/resources/artifactquery?view=graph-rest-1.0#restorableartifact-values) | The type of artifact to search. The possible values are: `message`, `unknownFutureValue`. |
| queryExpression | String | Specifies criteria to retrieve artifacts. |

### restorableArtifact values

| Member | Description |
| :--- | :--- |
| message | Mailbox message. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.artifactQuery",
  "queryExpression": "String",
  "artifactType": "String"
}
```
