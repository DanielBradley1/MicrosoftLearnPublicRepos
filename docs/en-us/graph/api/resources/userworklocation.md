<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userworklocation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-19 -->

# userWorkLocation resource type

Namespace: microsoft.graph

Represents the aggregated work location state for a user, computed from multiple signals: scheduled, automatic, and manual. It provides a consistent, privacy-aware way to indicate where a user works \(for example, office, remote, or time off\) and includes metadata that supports hybrid work scenarios.

- Precedence: manual > automatic > scheduled
- Precision: more granular wins \(for example, office + building > office\)

### Aggregation rules

- If manual location is set, it takes precedence immediately.
- Otherwise, if an automatic location exists, the most precise automatic signal wins.
- Otherwise, if a scheduled location exists, it's used as a fallback.
- If none exist, source = none; **workLocationType** = `unspecified`.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| placeId | String | Identifier of the place, if applicable. |
| source | workLocationSource | Indicates which layer wins the aggregation. The possible values are: `none`, `manual`, `scheduled`, `automatic`, `unknownFutureValue`. |
| workLocationType | workLocationType | Semantic type of the location. The possible values are: `unspecified`, `office`, `remote`, `timeOff`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userWorkLocation",
  "placeId": "String",
  "source": "String",
  "workLocationType": "String"
}
```
