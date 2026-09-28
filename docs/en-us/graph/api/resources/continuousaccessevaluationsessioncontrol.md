<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/continuousaccessevaluationsessioncontrol?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# continuousAccessEvaluationSessionControl resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Session control to control continuous access evaluation settings.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| mode | continuousAccessEvaluationMode | Specifies continuous access evaluation settings. The possible values are: `strictEnforcement`, `disabled`, `unknownFutureValue`, `strictLocation`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `strictLocation`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.continuousAccessEvaluationSessionControl",
  "mode": "String"
}
```
